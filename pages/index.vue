<template>
  <div>
    <v-list v-if="$vuetify.breakpoint.smAndUp" id="headerbar" flat class="pa-0">
      <v-layout>
        <v-flex lg5 xs8 sm8 md6>
          <v-list-item>
            <v-list-item-content class="ma-0">
              <v-list-item-title>
                <a herf="/">Name</a>
                <v-icon>mdi-menu-down</v-icon>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-flex>
        <v-flex lg3 hidden-xs-only hidden-sm-only md3>
          <v-list-item>
            <v-list-item-content class="ma-0">
              <v-list-item-title
                >Updated
                <v-icon>mdi-menu-down</v-icon>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-flex>
        <v-flex lg2 hidden-xs-only hidden-sm-only hidden-md-only>
          <v-list-item>
            <v-list-item-content class="ma-0">
              <v-list-item-title
                >Size
                <v-icon>mdi-menu-down</v-icon>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-flex>
        <v-flex lg2 xs4 sm4 md3>
          <v-list-item class="pa-0">
            <v-spacer></v-spacer>
            <v-list-item-action class="ma-0 mr-2">
              <v-btn icon x-small>
                <v-icon>mdi-view-grid</v-icon>
              </v-btn>
            </v-list-item-action>
            <v-list-item-action class="ma-0">
              <v-btn icon x-small @click.stop="drawerRight = !drawerRight">
                <v-icon>mdi-arrow-expand-right</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-flex>
      </v-layout>
      <template>
        <v-progress-linear indeterminate></v-progress-linear>
      </template>
    </v-list>
    <v-list id="contents" two-line flat class="pa-0">
      <v-divider></v-divider>
      <template v-for="(item, index) in items">
        <v-list-item :key="index" class="pa-0 listhover" @click="() => {}">
          <template>
            <v-layout>
              <v-flex lg5 xs8 sm8 md6>
                <v-list-item :key="index">
                  <v-list-item-avatar small class="ma-0 mr-3">
                    <v-icon
                      :class="[item.iconClass]"
                      v-text="item.icon"
                    ></v-icon>
                  </v-list-item-avatar>
                  <v-list-item-content class="ma-0">
                    <v-list-item-title v-text="item.title"></v-list-item-title>
                    <v-list-item-subtitle v-if="$vuetify.breakpoint.mdAndDown"
                      >120MB</v-list-item-subtitle
                    >
                  </v-list-item-content>
                </v-list-item>
              </v-flex>
              <v-flex lg3 hidden-xs-only hidden-sm-only md3>
                <v-list-item :key="index">
                  <v-list-item-content class="ma-0">
                    <v-list-item-title>
                      Today by Pham Minh Tu</v-list-item-title
                    >
                  </v-list-item-content>
                </v-list-item>
              </v-flex>
              <v-flex lg2 hidden-xs-only hidden-sm-only hidden-md-only>
                <v-list-item :key="index">
                  <v-list-item-content class="ma-0">
                    <v-list-item-title>120MB</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-flex>
              <v-flex lg2 xs4 sm4 md3>
                <v-list-item :key="index" class="pa-0">
                  <v-spacer></v-spacer>
                  <v-list-item-action class="ma-0 mr-2">
                    <v-menu left offset-overflow offset-y>
                      <template v-slot:activator="{ on }">
                        <v-btn fab x-small outlined v-on="on">
                          <v-icon small class="ma-0 pa-0"
                            >mdi-dots-horizontal</v-icon
                          >
                        </v-btn>
                      </template>
                      <v-list dense>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-share</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >Share</v-list-item-title
                          >
                        </v-list-item>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-download</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >Download</v-list-item-title
                          >
                        </v-list-item>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-star</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >Add to Favorites</v-list-item-title
                          >
                        </v-list-item>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-content-copy</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >Move or Copy</v-list-item-title
                          >
                        </v-list-item>
                        <v-divider></v-divider>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-settings</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >Setting</v-list-item-title
                          >
                        </v-list-item>
                        <v-list-item class="pa-0" @click="() => {}">
                          <v-list-item-icon class="mx-3">
                            <v-icon>mdi-dots-horizontal</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title class="mr-10"
                            >More Actions</v-list-item-title
                          >
                        </v-list-item>
                      </v-list>
                    </v-menu>
                  </v-list-item-action>
                  <v-list-item-action class="ma-0 mr-4">
                    <v-btn fab x-small outlined @click.stop="dialog = !dialog">
                      <v-icon small class="ma-0 pa-0">mdi-share</v-icon>
                    </v-btn>
                  </v-list-item-action>
                </v-list-item>
              </v-flex>
            </v-layout>
          </template>
        </v-list-item>
        <v-divider :key="index"></v-divider>
      </template>
    </v-list>
  </div>
</template>
<script>
export default {
  props: {
    source: String
  },
  data: () => ({
    sheet: false,
    sheetone: false,
    tiles: [
      { img: 'keep.png', title: 'Keep' },
      { img: 'inbox.png', title: 'Inbox' },
      { img: 'hangouts.png', title: 'Hangouts' },
      { img: 'messenger.png', title: 'Messenger' },
      { img: 'google.png', title: 'Google+' }
    ],
    tab: 0,
    tabs: [
      { text: 'My Files', icon: 'mdi-folder' },
      { text: 'Shared with me', icon: 'mdi-account-multiple' },
      { text: 'Starred', icon: 'mdi-star' },
      { text: 'Recent', icon: 'mdi-history' },
      { text: 'Offline', icon: 'mdi-check-circle' },
      { text: 'Uploads', icon: 'mdi-upload' },
      { text: 'Backups', icon: 'mdi-cloud-upload' }
    ],
    drawer: null,
    drawerRight: null,
    right: false,
    left: false,
    admins: [['Management', 'people_outline'], ['Settings', 'settings']],
    cruds: [
      ['Create', 'add'],
      ['Read', 'insert_drive_file'],
      ['Update', 'update'],
      ['Delete', 'delete']
    ],
    dialog: false,
    items: [
      {
        icon: 'mdi-zip-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Zip',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-folder-open',
        iconClass: 'cyan darken-4 white--text',
        title: 'Folder',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-video',
        iconClass: 'cyan darken-4 white--text',
        title: 'Video',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-music',
        iconClass: 'cyan darken-4 white--text',
        title: 'Music',
        subtitle: 'Jan 28, 2014'
      },
      {
        icon: 'mdi-image',
        iconClass: 'cyan darken-4 white--text',
        title: 'Image',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-file-document-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Text',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-file',
        iconClass: 'cyan darken-4 white--text',
        title: 'Phoytos',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-file-pdf-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Reccfgipes',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-file-powerpoint-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Wordrfk',
        subtitle: 'Jan 28, 2014'
      },
      {
        icon: 'mdi-file-word-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Phsxrfgotos',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-file-excel-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Recxsdfgipes',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-file-document-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Text',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-file',
        iconClass: 'cyan darken-4 white--text',
        title: 'Phoytos',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-file-pdf-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Reccfgipes',
        subtitle: 'Jan 17, 2014'
      },
      {
        icon: 'mdi-file-powerpoint-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Wordrfk',
        subtitle: 'Jan 28, 2014'
      },
      {
        icon: 'mdi-file-word-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Phsxrfgotos',
        subtitle: 'Jan 9, 2014'
      },
      {
        icon: 'mdi-file-excel-box',
        iconClass: 'cyan darken-4 white--text',
        title: 'Recxsdfgipes',
        subtitle: 'Jan 17, 2014'
      }
    ],
    drawers: ['Default (no property)', 'Permanent', 'Temporary'],
    primaryDrawer: {
      model: null,
      type: 'default (no property)',
      clipped: false,
      floating: false,
      mini: true
    },
    dense: true,
    fixedHeader: true,
    height: 100,
    initHeight: 0,
    initWidth: 0
  }),
  mounted() {
    // var initHeight;
    // initHeight = this.initHeight;
    // $('#nhaai').bind('touchmove', function(e) {
    //     //console.log(screen.height + " - " + screen.width);
    //     if (initHeight != screen.height) {
    //         alert('dang thay doi');
    //         console.log(screen.height + " - " + screen.width);
    //         e.preventDefault();
    //     }
    // });
    // $('#nhaai').bind('touchmove', function(e) {
    //     e.preventDefault();
    // });
    // // $().bind('touchmove', function(e) {
    // //     e.preventDefault();
    // // });
    // var ts;
    // $('#content').bind('touchstart', function(e) {
    //     ts = e.originalEvent.touches[0].clientY;
    // });
    // $('#content').bind('touchmove', function(e) {
    //     var te = e.originalEvent.changedTouches[0].clientY;
    //     var temp = ts - te;
    //     console.log(ts);
    //     console.log(te);
    //     if (temp > 0) {
    //         $('body').animate({ scrollTop: -temp }, '0');
    //         e.preventDefault();
    //         console.log('down');
    //     } else {
    //         $('body').animate({ scrollTop: temp }, '0');
    //         e.preventDefault();
    //         console.log('up');
    //     }
    // });
    // $('#content').css('padding-top', $('#appbar').height())
  },
  created() {
    // this.initHeight = $(window).height()
    // this.initWidth = screen.width;
    // alert(screen.height + " - " + screen.width);
    // alert($(window).height() + " - " + $(window).width());
    // // this.appheight = $(window).height();
    // // this.appwidth = $(window).width();
    // // alert($(window).height() + " - " + $(window).width());
  }
}
</script>
<style>
.theme--light.v-application {
  background: #fff !important;
}

.theme--dark.v-application {
  background: #424242 !important;
}

/*.listhover:hover {
    background-color: #f6fafd;
    border-bottom: 1px solid #d9e3e9;
    color: #002756;
}*/

/*.listhover {
    border-bottom: 1px solid #e8e8e8;
}*/

html {
  overflow: hidden !important;
}

body {
  height: 100%;
  position: fixed;
  width: 100%;
}

@media only screen and (max-width: 600px) {
  #contents {
    height: 100%;
    width: 100%;
    position: fixed;
    overflow-y: scroll;
    -webkit-overflow-scrolling: touch;
    /* iOS velocity scrolling */

    /*    padding-right: 550px !important;*/
    /*        padding-bottom: 500px !important;*/
    padding-bottom: calc(48px + 56px) !important;
  }

  .bottomselector {
    margin-bottom: 56px !important;
  }
}
</style>
