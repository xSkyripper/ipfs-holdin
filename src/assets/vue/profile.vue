<template>
    <div class="page-content">
        <f7-block-title>
            <h2>Profile</h2>
        </f7-block-title>

        <f7-list>
            <f7-list-group>
                <f7-list-item title="System status" group-title></f7-list-item>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">wifi</i></div>
                        <div class="item-title">Network</div>
                        <div class="item-after">
                            <span v-if="sharedState.statusNetwork" class="color-green">
                                {{sharedState.statusNetwork}} - Online
                            </span>
                            <span class="color-red" v-else>
                                Offline
                            </span>
                        </div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">location_on</i></div>
                        <div class="item-title">Location</div>
                        <div class="item-after">
                            <span v-if="sharedState.statusLocation" class="color-green">
                                Online
                            </span>
                            <span class="color-red" v-else>
                                Offline
                            </span>
                        </div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">archive</i></div>
                        <div class="item-title">IPFS Repo</div>
                        <div class="item-after">
                            <span v-if="sharedState.statusIpfsRepo" class="color-green">
                                Online
                            </span>
                            <span class="color-red" v-else>
                                Offline
                            </span>
                        </div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">code</i></div>
                        <div class="item-title">IPFS Daemon</div>
                        <div class="item-after">
                            <span v-if="sharedState.statusIpfsDaemon" class="color-green">
                                Online
                            </span>
                            <span class="color-red" v-else>
                                Offline
                            </span>
                        </div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">comment</i></div>
                        <div class="item-title">IPFS PubSub</div>
                        <div class="item-after">
                            <span v-if="sharedState.statusIpfsPubSub" class="color-green">
                                Online
                            </span>
                            <span class="color-red" v-else>
                                Offline
                            </span>
                        </div>
                    </div>
                </li>
            </f7-list-group>
            <f7-list-group>
                <f7-list-item title="User status" group-title></f7-list-item>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">account_box</i></div>
                        <div class="item-title">Username</div>
                        <div class="item-after">{{sharedState.username}}</div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">location_on</i></div>
                        <div class="item-title">Location exact</div>
                        <div class="item-after">{{sharedState.locationExact.lon}}, {{sharedState.locationExact.lat}}
                        </div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">location_city</i></div>
                        <div class="item-title">Location zone</div>
                        <div class="item-after">{{sharedState.locationZone.zoneId}}</div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">timer</i></div>
                        <div class="item-title">Zone Updater Delay</div>
                        <div class="item-after">{{sharedState.zoneUpdaterDelay}} min(s)</div>
                    </div>
                </li>
                <li class="item-content">
                    <div class="item-inner">
                        <div class="item-media"><i class="material-icons">speaker_notes_off</i></div>
                        <div class="item-title">Messages Time To Live</div>
                        <div class="item-after">{{sharedState.messagesTTL}} day(s)</div>
                    </div>
                </li>
            </f7-list-group>

            <f7-list-group>
                <f7-list-item title="My Last 10 Messages" group-title></f7-list-item>
                <a v-for="myMsg in sharedState.myMessages" :href="'/message/'+myMsg.id" class="item-link">
                    <div class="item-content">
                        <div class="item-inner">
                            <div class="item-media">
                                <i v-if="myMsg.type === 'alert'" class="color-red material-icons">warning</i>
                                <i v-else-if="myMsg.type === 'warn'" class="material-icons color-amber">error</i>
                                <i v-else="myMsy.type === 'info'" class="material-icons color-white">info</i>
                            </div>
                            <div class="item-title">{{myMsg.locationZone}}</div>
                            <div class="item-after">{{myMsg.time}} {{myMsg.day}}.{{myMsg.month}}.{{myMsg.year}}</div>
                        </div>
                    </div>
                </a>
            </f7-list-group>
        </f7-list>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                sharedState: this.$myStore.state,
                privateState: {}
            }
        },
        props: {},
        methods: {}
    }
</script>

<style>

</style>
