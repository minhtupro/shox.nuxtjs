<template>
  <v-app id="nhaai">
    <v-navigation-drawer
      v-if="$vuetify.breakpoint.lgAndUp"
      v-model="drawerRight"
      app
      right
    >
      <template>
        <v-card :loading="loading" flat>
          <v-card-title>Cafe Badilico</v-card-title>
          <v-card-text>
            <v-row align="center">
              <v-rating
                :value="4.5"
                color="amber"
                half-increments
                dense
                size="14"
                readonly
              ></v-rating>
              <div class="grey--text ml-4">4.5 (413)</div>
            </v-row>
            <div class="my-4 subtitle-1 black--text">
              $ • Italian, Cafe
            </div>
            <div>
              Small plates, salads & sandwiches an inteimate setting with 12
              indoor seats plus patio seating.
            </div>
          </v-card-text>
          <v-divider class="mx-4"></v-divider>
          <v-card-text>
            <div class="title text--primary">Tonight's availability</div>
            <v-chip-group
              v-model="selection"
              active-class="deep-purple accent-4 white--text"
              column
            >
              <v-chip>5:30PM</v-chip>
              <v-chip>7:30PM</v-chip>
              <v-chip>8:00PM</v-chip>
              <v-chip>9:00PM</v-chip>
            </v-chip-group>
          </v-card-text>
          <v-card-actions>
            <v-btn color="deep-purple accent-4" text @click="reserve">
              Reserve
            </v-btn>
          </v-card-actions>
        </v-card>
      </template>
    </v-navigation-drawer>
    <v-navigation-drawer
      v-model="drawer"
      app
      :clipped="$vuetify.breakpoint.lgAndUp"
    >
      <v-list nav dense>
        <v-list-item-group v-model="tab" color="primary">
          <template v-for="(tab, index) in tabs">
            <v-list-item :key="index">
              <v-list-item-icon>
                <v-icon v-text="tab.icon"></v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="tab.text"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </template>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app dense :clipped-left="$vuetify.breakpoint.lgAndUp">
      <v-btn icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-app-bar-nav-icon
        v-if="$vuetify.breakpoint.smAndUp"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-divider class="mr-3" vertical></v-divider>
      <v-toolbar-title class="title mr-5">Shox Epress</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-divider class="ml-3" vertical></v-divider>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content id="content">
      <v-container class="pa-0">
        <template>
          <v-list
            v-if="$vuetify.breakpoint.smAndUp"
            id="headerbar"
            flat
            class="pa-0"
          >
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
                    <v-btn
                      icon
                      x-small
                      @click.stop="drawerRight = !drawerRight"
                    >
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
              <v-list-item
                :key="index"
                class="pa-0 listhover"
                @click="() => {}"
              >
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
                          <v-list-item-title
                            v-text="item.title"
                          ></v-list-item-title>
                          <v-list-item-subtitle
                            v-if="$vuetify.breakpoint.mdAndDown"
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
                          <v-btn
                            fab
                            x-small
                            outlined
                            @click.stop="dialog = !dialog"
                          >
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
        </template>
      </v-container>
    </v-content>
    <template>
      <div class="text-center">
        <v-dialog v-model="dialog" width="500">
          <v-card>
            <v-card-title class="headline mb-5"
              >Share
              <v-spacer></v-spacer>
              <v-btn
                class="pa-0 ma-0"
                outlined
                x-small
                icon
                @click="dialog = false"
              >
                <v-icon>mdi-close</v-icon>
              </v-btn>
            </v-card-title>
            <v-card-text>
              <template>
                <v-card-title class="pa-0 subtitle-1"
                  >Invite People</v-card-title
                >
                <v-text-field outlined required></v-text-field>
                <v-card-title class="pa-0 ma-0 subtitle-1"
                  >Invite as Editor</v-card-title
                >
                <v-select :items="items" outlined required>items</v-select>
                <v-divider class="my-5"></v-divider>
                <v-card-title class="pa-0 subtitle-1">Share Link</v-card-title>
                <v-switch class="ma-0" label="Enable shared link"></v-switch>
              </template>
            </v-card-text>
          </v-card>
        </v-dialog>
      </div>
    </template>
    <template>
      <v-bottom-navigation v-model="bottomNav" app grow>
        <v-btn @click.stop="sheet = !sheet">
          <span>Files</span>
          <v-icon>mdi-folder-open</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet1 = !sheet1">
          <span>Upload</span>
          <v-icon>mdi-upload</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet = !sheet">
          <span>Add</span>
          <v-icon>mdi-plus</v-icon>
        </v-btn>
        <v-divider vertical></v-divider>
        <v-btn @click.stop="sheet1 = !sheet1">
          <span>User</span>
          <v-icon>mdi-account</v-icon>
        </v-btn>
      </v-bottom-navigation>
    </template>
    <template>
      <v-bottom-sheet v-model="sheet" app content-class="bottomselector">
        <v-list>
          <v-list-item
            v-for="tile in tiles"
            :key="tile.title"
            @click="sheet = false"
          >
            <v-list-item-avatar>
              <v-avatar size="32px" tile>
                <img
                  :src="
                    `https://cdn.vuetifyjs.com/images/bottom-sheets/${tile.img}`
                  "
                  :alt="tile.title"
                />
              </v-avatar>
            </v-list-item-avatar>
            <v-list-item-title>{{ tile.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-bottom-sheet>
      <v-divider></v-divider>
    </template>
    <template>
      <v-bottom-sheet v-model="sheetone" app content-class="bottomselector">
        <v-list>
          <v-list-item
            v-for="tile in tiles"
            :key="tile.title"
            @click="sheetone = false"
          >
            <v-list-item-avatar>
              <v-avatar size="32px" tile>
                <img
                  :src="
                    `https://cdn.vuetifyjs.com/images/bottom-sheets/${tile.img}`
                  "
                  :alt="tile.title"
                />
              </v-avatar>
            </v-list-item-avatar>
            <v-list-item-title>{{ tile.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-bottom-sheet>
      <v-divider></v-divider>
    </template>
  </v-app>
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
