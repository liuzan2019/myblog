1.用户分群和用户细查总数对不上

2.最近会话时间有2033年的，但是用户细查里面的最近会话时间不是2033年

3.是否多用户属性过滤条件没有起作用





629dd49f88e51e28bdcd566a

```json
{
    "indicators": [
        {
            "op": "",
            "type": 6,
            "eventNamesInVE": [],
            "hasEventFilter": false,
            "hasUserFilter": false,
            "hasUserGroupFilter": false,
            "userGroupFilterCount": 0,
            "filterRelationType": ""
        }
    ],
    "global": {
        "relationType": 0,
        "filters": [
            {
                "propName": "是否是多设备用户",
                "propId": "$isMultipleDevicesUser",
                "propType": 1,
                "selector": 9,
                "payload": [
                    true
                ],
                "propValType": 2
            }
        ],
        "hasEventFilter": false,
        "hasUserFilter": false,
        "hasUserGroupFilter": false
    },
    "dimensions": [
        {
            "propId": "$isMultipleDevicesUser",
            "propName": "是否是多设备用户",
            "propValType": 2,
            "propType": 1
        },
        {
            "propId": "$lastManufacturer",
            "propName": "最近设备厂商",
            "propValType": 0,
            "propType": 1
        },
        {
            "propId": "$lastBrand",
            "propName": "最近设备品牌",
            "propValType": 0,
            "propType": 1
        },
        {
            "propId": "$lastModel",
            "propName": "最近设备型号",
            "propValType": 0,
            "propType": 1
        }
    ],
    "majorDimension": "$isMultipleDevicesUser"
}
```

