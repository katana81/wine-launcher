<template>
    <div class="item-point card-box m-b-10" @mouseenter="hover">
        <div class="item-point__background"></div>

        <div class="table-box opport-box">
            <div class="table-detail">
                <div class="member-info">
                    <h4 class="m-0 m-b-10">
                        <span class="badge badge-success" :class="{'badge-success' : active, 'badge-danger': !active}">
                            .
                        </span>
                        &nbsp;
                        <b>{{patch.sort}} - {{patch.name}}</b>
                        &nbsp;
                    </h4>
                    <table class="text-dark text-muted tr-title">
                        <tbody>
                        <tr>
                            <td>{{ $t('labels.version') }}</td>
                            <td><span>{{patch.version}}</span></td>
                        </tr>
                        <tr>
                            <td>{{ $t('labels.arch') }}</td>
                            <td>
                                <span>{{getArch()}}</span>
                                <span v-if="patch.arch !== wine.status.arch" class="m-l-10 label label-danger">
                                    {{ $t('labels.incompatible') }}
                                </span>
                            </td>
                        </tr>
                        <tr>
                            <td>{{ $t('labels.folder') }}</td>
                            <td><span>{{patch.code}}</span></td>
                        </tr>
                        </tbody>
                    </table>
                </div>
            </div>

            <div class="table-detail item-point__info">
                <p v-if="patch.size" class="text-dark m-b-10 text-right">
                    <span class="label label-inverse">{{ $t('labels.size') }}: {{patch.size_formatted}}</span>
                </p>
            </div>

            <div class="table-detail item-point__button-block">
                <template v-if="!patch.created">
                    <PopupCommand v-if="patch" :patch="patch.patch" ref="popup"/>
                </template>
                <PopupPatch v-if="patch" :patch="patch.patch" ref="popup"/>
                <PopupRemove v-if="patch" :item="patch"/>
            </div>
        </div>
    </div>
</template>

<script>
    import PopupPatch   from "./PopupPatch";
    import PopupCommand from "./PopupCommand";
    import PopupRemove  from "./PopupRemove";
    import Collects     from "../../helpers/collects";

    export default {
        name:       "ItemPatch",
        components: {
            PopupPatch,
            PopupCommand,
            PopupRemove,
        },
        props:      {
            patch: Object,
        },
        data() {
            return {
                wine: this.$store.state.wine,
            };
        },
        methods:    {
            getArch() {
                return Collects.arch[this.patch.arch];
            },
            hover() {
                window.app.getAudioButton().hover();
            },
        },
        computed:   {
            active() {
                return this.patch.active && this.patch.created;
            },
        }
    }
</script>

<style lang="less" scoped>
    .item-point__info {
        text-align: left;
    }

    .badge {
        position: relative;
        color: transparent;
        top: -2px;
        width: 13px;
        height: 13px;
        margin-right: 5px;
    }

    .tr-title td {
        padding-right: 10px;
    }

    .item-point__button-block > div {
        margin-top: 10px;
        margin-bottom: 10px;
    }
</style>