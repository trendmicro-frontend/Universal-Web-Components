<template>
    <div class="license">
        <div v-if="showSeg">
            <span class="tmicon tmicon-help"></span>
            <span class="icon-name" v-show="is_expire === false">
                {{ $t("license_in_active.seg_notice")}} 
                <a href="javascript:;" @click="license_jump(1)">{{$t("license_in_active.seg_link")}}</a>
            </span>
            <span class="icon-name" v-show="is_expire === true">
                {{ $t("license_in_active.seg_expire")}} 
                <a href="javascript:;" @click="license_jump(1)">{{$t("license_in_active.seg_link")}}</a>
            </span>    
        </div>
            <div v-if="showAtp">
            <span class="tmicon tmicon-help"></span>
            <span class="icon-name" v-show="is_expire === false">
                {{ $t("license_in_active.atp_notice")}} 
                <a href="javascript:;" @click="license_jump(0)">{{$t("license_in_active.atp_link")}}</a>
            </span>
            <span class="icon-name" v-show="is_expire === true">
                {{ $t("license_in_active.atp_expire")}} 
                <a href="javascript:;" @click="license_jump(0)">{{$t("license_in_active.atp_link")}}</a>
            </span>
        </div>
    </div>
</template>
<script>
    export default {
        name: 'TmVueLicenseInactive',
        i18n:i18n,
        props:{
            type:{
                type:String,
                default:"seg",
            },
            expired:{
                type:Boolean,
                default:false
            }
        },
        computed:{
        	data_type(){
        		return this.type?this.type:'seg';
        	},
            is_expire(){
                return typeof(this.expired) !== "undefined"?this.expired == "true":false;
            },
            showSeg(){
                return this.data_type =='seg';
            },
            showAtp(){
                return this.data_type =='atp';
            }
        },
        methods: {
            license_jump:function(type){
                var top_parent_click = window.parent.license_click || window.parent.parent.license_click;
                top_parent_click(type);
            }            
        }
    }
</script>