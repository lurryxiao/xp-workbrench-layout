<template>
    <v-layout name="城市地图工作台" :sideBarItems="items" :showTags="false" :noTagsSmallStyle="true">
    </v-layout>
</template>

<script lang="ts">
import { onMounted, reactive, Ref, ref, toRefs } from 'vue'
import { VLayout } from '../components'

export default {
    components: {
        VLayout,
    },
    setup() {
        const data = reactive({
            items: [] as RouteListItem[],
        })
        const getItems = () => {
            return new Promise<RouteListItem[]>((resolve) => {
                resolve([
                    {
                        icon: "Monitor",
                        index: "/dashboard",
                        title: "综合",
                    },
                    {
                        icon: "Operation",
                        index: "2",
                        title: "属性管理",
                        subs: [
                            {
                                index: "/propertySetting",
                                title: "配色管理",
                                link: "/propertySetting",
                            },
                            {
                                index: "/propertySetting2",
                                title: "随便",
                            }
                        ]
                    },
                    {
                        icon: "Operation",
                        index: "3",
                        title: "另外管理",
                        subs: [
                            {
                                index: "/propertySettingcc",
                                title: "配色管理2",
                                link: "http://www.baidu.com",
                            },
                            {
                                index: "/propertySetting2",
                                title: "随便",
                            }
                        ]
                    },
                    {
                        icon: "Monitor",
                        index: "",
                        title: "测试",
                        link: "http://www.baidu.com",
                    },
                ])
            })
        }
        onMounted(async () => {
            data.items = await getItems()
        })
        // const items: Ref< RouteListItem[] > = ref([
        //     {
        //         icon: "Monitor",
        //         index: "/dashboard",
        //         title: "综合",
        //     },
        //     {
        //         icon: "Operation",
        //         index: "2",
        //         title: "属性管理",
        //         subs: [
        //             {
        //                 index: "/propertySetting",
        //                 title: "配色管理",
        //                 link: "/propertySetting",
        //             },
        //             {
        //                 index: "/propertySetting2",
        //                 title: "随便",
        //             }
        //         ]
        //     },
        //     {
        //         icon: "Operation",
        //         index: "3",
        //         title: "另外管理",
        //         subs: [
        //             {
        //                 index: "/propertySettingcc",
        //                 title: "配色管理2",
        //                 link: "http://www.baidu.com",
        //             },
        //             {
        //                 index: "/propertySetting2",
        //                 title: "随便",
        //             }
        //         ]
        //     },
        //     {
        //         icon: "Monitor",
        //         index: "",
        //         title: "测试",
        //         link: "http://www.baidu.com",
        //     },
        // ])
        return {
            ...toRefs(data),
        }
    }
}
</script>
