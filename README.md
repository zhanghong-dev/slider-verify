#portal-component__slider-verify

### 参数 value
```
滑块的 “目标” 位置
它是一个有两个数字的数组，表示了水平、垂直

初始值
value = [ -1024, -1024 ]

正常值
value = [ Math.random(), Math.random() ]
```

### 参数 toleranceValue
```
滑块拖拽完成时，与 “目标” 位置的差值的允许量
0 ~ 1 之间的小数

具体来说
因为当一个人在拖拽滑块后，很难完全落在 “目标” 位置上
所以可以有个允许的误差量

不允许有误差量
toleranceValue = 0

推荐的误差量
toleranceValue = .015
```

### @loading
```
在组件 created 时被触发
在滑块拖拽完成并 “错误” 时被触发

例：
<template>
    <portal-component__slider-verify
        v-bind="sliderVerify"
        @loading="sliderVerifyLoading"
        ...
</template>
<script>
    export default {
        components: {
            portalComponent__sliderVerify
        },
        methods: {
            sliderVerifyLoading($done) {

                var h = () => {

                    sliderVerify.value = [
                        Math.random(),
                        Math.random()
                    ];

                    $done();
                };

                // 假设请求了服务器
                setTimeout(h, 400);

            },
            ...
        },
        data() {

            return {
                sliderVerify: {
                    value: [ -1024, -1024 ],
                    ...
                },
                ...
            };

        }
    }
</script>

```

### @success
```
在滑块拖拽完成并 “正确” 时被触发
```

### @error
```
在滑块拖拽完成并 “错误” 时被触发
```
