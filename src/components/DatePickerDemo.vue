<template>
    <div class="hello">
        <vue-datepicker-local v-model="range" range-separator=" 至 " show-buttons @confirm="confirmDate" format="YYYY-MM-DD" :disabled-date="disabledDate"/>
    </div>
</template>

<script>
import VueDatepickerLocal from 'vue-datepicker-local'

export default {
    components: {
        VueDatepickerLocal
    },
    data () {
        return {
            range: [this.getDateObj(this.getDateAddOrMinus(-6)), this.getDateObj(this.getDateAddOrMinus(0))]
        }
    },
    watch: {
        // range发生变化，这个函数就会执行
        range () {
            console.log(this.range)
        }
    },
    methods: {
        confirmDate (value) {
            console.log(value)
            console.log(this.getDateStr(value[0]))
            console.log(this.getDateStr(value[1]))
        },
        disabledDate (time) {
            return time.getTime() > Date.now()
        },
        // 返回日期字符串，格式：20170908
        // 参数：日期对象
        getDateStr: (dateObj) => {
            let y = dateObj.getFullYear()
            let m = dateObj.getMonth() + 1
            let d = dateObj.getDate()
            let mStr = ''
            let dStr = ''
            if (m < 10) {
                mStr = '0' + m
            } else {
                mStr = m.toString()
            }
            if (d < 10) {
                dStr = '0' + d
            } else {
                dStr = d.toString()
            }
            return y.toString() + mStr + dStr
        },
        // 返回值：根据日期格式：20171103，返回日期对象
        // dateStr格式：20171011
        getDateObj: (dateStr) => {
            let dateObj = new Date(dateStr.substr(0, 4), dateStr.substr(4, 2) - 1, dateStr.substr(6, 2))
            return dateObj
        },
        // 返回值：增减后的日期，格式：20171103
        // addDayCount: 增减的日期，可以是：0（今日），-1（昨日），30（30日后）
        getDateAddOrMinus: (addDayCount) => {
            let dd = new Date()
            dd.setDate(dd.getDate() + addDayCount)
            let y = dd.getFullYear()
            let m = dd.getMonth() + 1
            let d = dd.getDate()
            let mStr = ''
            let dStr = ''
            if (m < 10) {
                mStr = '0' + m
            } else {
                mStr = m.toString()
            }
            if (d < 10) {
                dStr = '0' + d
            } else {
                dStr = d.toString()
            }
            return y.toString() + mStr + dStr
        }
    }
}
</script>

<style>
    .datepicker-range {
        min-width: 260px !important;
    }
    .datepicker>input {
        border-radius: 4px;
    }

    .datepicker-range .datepicker-popup {
        border-radius: 4px;
    }

    .calendar-date-selected, .calendar-date-selected:hover {
        border-radius: 4px;
    }
    .datepicker__buttons .datepicker__button-cancel {
        border-radius: 4px;
    }

    .datepicker__buttons .datepicker__button-select {
        border-radius: 4px;
    }
    h1, h2 {
        font-weight: normal;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }
</style>
