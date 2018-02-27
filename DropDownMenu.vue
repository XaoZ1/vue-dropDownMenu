<template>
    <div class="dropDown-wrap">
        <span class="title-name" :class="optionData.titleInfo == '' ? '' : 'select'">
            {{optionData.titleInfo == '' ? titleName : optionData.titleInfo}}
            <i class="iconfont icon-arrow-down drop-triangle" v-if="optionData.titleInfo ==''"></i>
            <i class="el-icon-circle-close" title="清除" @click="clearTitleInfo" v-else></i>
        </span>
        <ul class="drop-list">
            <li :class="{active: actIndex == index}" v-for="(item, index) in propList" @click="itemClick(item, index)">{{getDataType(dataType, item)}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: [
        'titleName',
        'propList',
        'dataType',
        'dataDataType'
    ],
    data () {
        return {
            actIndex: null,
            optionData: {
                titleInfo: ''
            },
            returnData: {
                operateId: '',
                operateName: '',
                operateIndex: '',
            },
            customDiaData: {
                type: '',
                value: ''
            }
        }
    },
    methods: {
        getDataType (type, item) {
            //console.log(item)
            switch (this.dataType) {
                case '柜组':
                    return item.counterName
                case '柜组1':
                    return item.counterName
                case '店铺':
                    return item.shopName
                case '分销商':
                    return item.shopName
                case '库位':
                    return item.repositoryName
                case '库位1':
                    return item.repositoryName
                case '产品类别':
                    return item
                case '单据状态':
                    return item
                case '供应商':
                    return item.supplierName
                case '制单人':
                    return item.username
                case '销售人':
                    return item.username
                case '审核人':
                    return item.username
                case '收货人':
                    return item.username
                case 'customDia':
                    return item
                case '成色':
                    return item.classesName
                case '属性':
                    return item.name
                case '位置':
                    return item.name
                case '会员类型':
                    return item.name
                case '会员级别':
                    return item.name
                case '跟进目的':
                    return item.name
                case '跟进状态':
                    return item.name
                case '购买时间':
                    return item.name
                case '发送人' :
                    return item.userName
            }
        },
        itemClick (item, index) {
            this.actIndex = index
            this.returnData.operateIndex = index
            //console.log(item)
            switch (this.dataType) {
                case '柜组':
                    this.optionData.titleInfo = item.counterName
                    this.returnData.operateId = item.counterId
                    this.returnData.operateName = item.counterName
                    break;
                case '柜组1':
                    this.optionData.titleInfo = item.counterName
                    this.returnData.operateId = item.counterId
                    this.returnData.operateName = item.counterName
                    break;
                case '店铺':
                    this.optionData.titleInfo = item.shopName
                    this.returnData.operateId = item.shopId
                    this.returnData.operateName = item.shopName
                    break;
                case '发送人':
                    this.optionData.titleInfo = item.userName
                    this.returnData.operateId = item.userId
                    this.returnData.operateName = item.userName
                    break;
                case '分销商':
                    this.optionData.titleInfo = item.shopName
                    this.returnData.operateId = item.shopId
                    this.returnData.operateName = item.shopName
                    break;
                case '库位':
                    this.optionData.titleInfo = item.repositoryName
                    this.returnData.operateId = item.repositoryId
                    this.returnData.operateName = item.repositoryName
                    break;
                case '库位1':
                    this.optionData.titleInfo = item.repositoryName
                    this.returnData.operateId = item.repositoryId
                    this.returnData.operateName = item.repositoryName
                    break;
                case '产品类别':
                    this.optionData.titleInfo = item
                    if (item == '计重类') {
                        this.returnData.operateId = 1
                    } else {
                        this.returnData.operateId = 2
                    }
                    this.returnData.operateName = ''
                    break;
                case '单据状态':
                    this.optionData.titleInfo = item
                    if (item == '待审核') {
                        this.returnData.operateId = 1
                    } else if (item == '审核中') {
                        this.returnData.operateId = 2
                    } else {
                        this.returnData.operateId = 3
                    }
                    this.returnData.operateName = ''
                    break;
                case '供应商':
                    this.optionData.titleInfo = item.supplierName
                    this.returnData.operateId = item.supplierId
                    this.returnData.operateName = item.supplierName
                    break;
                case '制单人':
                    this.optionData.titleInfo = item.username
                    this.returnData.operateId = item.userId
                    this.returnData.operateName = item.username
                    break;
                case '销售人':
                    this.optionData.titleInfo = item.username
                    this.returnData.operateId = item.userId
                    this.returnData.operateName = item.username
                    break;
                case '审核人':
                    this.optionData.titleInfo = item.username
                    this.returnData.operateId = item.userId
                    this.returnData.operateName = item.username
                    break;
                case '收货人':
                    this.optionData.titleInfo = item.username
                    this.returnData.operateId = item.userId
                    this.returnData.operateName = item.username
                    break;
                case '成色':
                    this.optionData.titleInfo = item.classesName
                    this.returnData.operateId = item.classesId
                    this.returnData.operateName = item.classesName
                    break;
                case '属性':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '位置':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '会员类型':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '会员级别':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '跟进状态':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '跟进目的':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case '购买时间':
                    this.optionData.titleInfo = item.name
                    this.returnData.operateId = item.type
                    this.returnData.operateName = item.name
                    break;
                case 'customDia':
                    this.optionData.titleInfo = item
                    if (this.dataDataType == '成色名称-计重') {
                        this.customDiaData.type = 1
                        switch (item) {
                            case '不选':
                                this.customDiaData.value = ''
                            break;
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    } else if (this.dataDataType == '宝石名称-计重') {
                        this.customDiaData.type = 2
                        switch (item) {
                            case '不选':
                                this.customDiaData.value = ''
                            break;
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    } else if (this.dataDataType == '首饰类别-计重') {
                        this.customDiaData.type = 3
                        switch (item) {
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    } else if (this.dataDataType == '成色名称-计件') {
                        this.customDiaData.type = 4
                        switch (item) {
                            case '不选':
                                this.customDiaData.value = ''
                            break;
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    } else if (this.dataDataType == '宝石名称-计件') {
                        this.customDiaData.type = 5
                        switch (item) {
                            case '不选':
                                this.customDiaData.value = ''
                            break;
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    } else if (this.dataDataType == '首饰类别-计件') {
                        this.customDiaData.type = 6
                        switch (item) {
                            case '大类':
                                this.customDiaData.value = 1
                            break;
                            case '小类':
                                this.customDiaData.value = 2
                            break;
                        }
                    }
                    this.$emit('infoBack', {type: this.customDiaData.type, value: this.customDiaData.value})
                    break;

            }
            let _data = Object.assign(this.returnData ,item)
            this.$emit("dropReturn", {item: _data, type: this.dataType})
        },
        clearTitleInfo () {
            this.optionData.titleInfo = ''
            this.$emit("clearInfo", {type: this.dataType})
            this.actIndex = null
        }
    }
}
</script>

<style lang="scss" scoped>
.dropDown-wrap {
    display: inline-block;
    position: relative;
    cursor: pointer;
    &:after{
    content:'';
        border: 6px solid transparent;
        //border-bottom-color: #fff;
        width: 0;
        height: 0;
        position: absolute;
        top: 38px;
        right:0px;
        z-index: 102;
        transition: all .3s;
        margin-left: -3px;
    }
    &:hover{
        background:#e0ecf7;
        color:#3195f5;
        >ul{
            opacity: 1;
            visibility: visible;
            top:30px;
        }
        &:after{
            top: 18px;
            border-bottom-color: #fff;
        }
        >.title-name .drop-triangle {
            transform: rotate(180deg);
            //color:#2993f8;
        }
        >.title-name {
            color:#3195f5;
        }
        .title-name .el-icon-circle-close {
            color:#2993f8;
        }
    }
    .title-name {
        padding: 0 8px;
        &.select{
            //color: #333;
        }
        color:#666;
        text-align: right;
        display: block;
        height: 30px;
        font-weight: bold;
        font-size: 14px;
        line-height: 30px;
        .drop-triangle {
            font-size:12px;
            display: inline-block;
            //transform: scale(120%, 120%) !important;
            transition: all .3s;
            transform-origin: center center;
        }
        .el-icon-circle-close {
            position: absolute;
            top: -4px;
            right: -4px;
            font-size:10px;
            color:#ccc;
            cursor: pointer;
        }
        // .el-icon-circle-close:hover {
        //     color:#2993f8;
        // }
    }
    .drop-list {
        overflow: hidden;
        opacity: 0;
        visibility: hidden;
        transition: all .3s;
        background:#fff;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        border-radius: 4px;
        position: absolute;
        letter-spacing: 0;;
        top: 50px;
        right: -20px;
        z-index: 101;
        max-height: 300px;
        overflow: hidden;
        overflow-y: auto;
        li {
            text-align: left;
            height: 42px;
            line-height: 42px;
            width: 130px;
            font-size: 13px;
            color:#333;
            white-space: nowrap;
            box-sizing: border-box;
            padding-left: 10px;
            border-bottom: 1px solid #f1f2f3;
            border-left: 4px solid transparent;
            cursor: pointer;
            &.active{
                color: #2993f8;
                border-left-color: #2993f8;
            }
        }
        li:before {
            content: '';
            height: 100%;
            width: 3px;
            position: absolute;
            left: 0;
            top: 0;
        }
        li:hover {
            background:#f6f7f8;
        }
        li.active:before {
            display: none;
        }
    }
}

</style>
