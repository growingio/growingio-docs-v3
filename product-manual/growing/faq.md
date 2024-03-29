# 常见问题

## 产品使用部分 <a href="#chan-pin-shi-yong-bu-fen" id="chan-pin-shi-yong-bu-fen"></a>

### 1. Android手机在自己的应用中使用Deeplink会报错？ <a href="#1-android-shou-ji-zai-zi-ji-de-ying-yong-zhong-shi-yong-deeplink-hui-bao-cuo" id="1-android-shou-ji-zai-zi-ji-de-ying-yong-zhong-shi-yong-deeplink-hui-bao-cuo"></a>

目前不支持在Android Web View中打开Deeplink，请根据使用场景调整活动页面。

### **2. 权限配置，可以根据渠道配置权限吗？为什么配置权限后该用户能看到所有的数据或者不能看到数据？** <a href="#2-quan-xian-pei-zhi-ke-yi-gen-ju-qu-dao-pei-zhi-quan-xian-ma-wei-shi-mo-pei-zhi-quan-xian-hou-gai-yo" id="2-quan-xian-pei-zhi-ke-yi-gen-ju-qu-dao-pei-zhi-quan-xian-ma-wei-shi-mo-pei-zhi-quan-xian-hou-gai-yo"></a>

目前只能根据活动名称来分配权限。需要您先找您的GIO客户成功经理开启高级权限功能，然后在用户管理页面给该用户配置广告监测的数据查看等功能，再通过广告监测里面的权限管理进行配置。

### **3. 点击监测链接的时候可以拿到用户的设备号吗？** <a href="#3-dian-ji-jian-ce-lian-jie-de-shi-hou-ke-yi-na-dao-yong-hu-de-she-bei-hao-ma" id="3-dian-ji-jian-ce-lian-jie-de-shi-hou-ke-yi-na-dao-yong-hu-de-she-bei-hao-ma"></a>

如果是服务器对接的渠道（比如今日头条广点通）这样的渠道，是可以拿到用户的设备号的（今日头条服务器回传给GIO），如果是302渠道（自己创建的渠道）点击的时候只能拿到用户的IP+UA。

### **4. 异常点击是什么？** <a href="#4-yi-chang-dian-ji-shi-shi-mo" id="4-yi-chang-dian-ji-shi-shi-mo"></a>

在选择时间内被判定为作弊广告的点击量，反作弊规则可根据以往投放经验进行时间窗口与点击上限的调整。（例如自定义配置：时间窗为1小时，IP点击上限为100次，那么存在某一IP在1小时内进行了100次点击，这100次都会被判定为作弊点击）。

## 数据质量部分 <a href="#shu-ju-zhi-liang-bu-fen" id="shu-ju-zhi-liang-bu-fen"></a>

### **1. 在广告监测中创建了几条监测链接，每条都有新访问用户量统计，请问我们统计是否有排重逻辑？比如用户1 首次访问 a 链接，a 链接记一次新访问用户，又访问一次 b 链接，b 链接是否又统 计一遍新访问用户？** <a href="#1-zai-guang-gao-jian-ce-zhong-chuang-jian-le-ji-tiao-jian-ce-lian-jie-mei-tiao-du-you-xin-fang-wen-y" id="1-zai-guang-gao-jian-ce-zhong-chuang-jian-le-ji-tiao-jian-ce-lian-jie-mei-tiao-du-you-xin-fang-wen-y"></a>

我们这边的归因逻辑是就近归因。比如在同一个小时内先点击了A，再点击了B，这样会归因到B。在3点的时候点击了A，4点的时候点击了B，那么按小时看，3点会被归因到A，4点会被归因到B。如果按天看，先点A，再点B，新访问用户量会被归因到B。

### **2. 在广告监测中的激活为什么大于单图里面的新访问用户量？** <a href="#2-zai-guang-gao-jian-ce-zhong-de-ji-huo-wei-shi-mo-da-yu-dan-tu-li-mian-de-xin-fang-wen-yong-hu-lian" id="2-zai-guang-gao-jian-ce-zhong-de-ji-huo-wei-shi-mo-da-yu-dan-tu-li-mian-de-xin-fang-wen-yong-hu-lian"></a>

广告监测的激活数据，卸载超过48小时后再重新安装，就会重新统计算一次激活。单图里的新访问用户量指的是过去365天第一次访问您App的用户。

### **3. 在广告监测中的新登录为什么和单图里面的新登录用户量不一致？** <a href="#3-zai-guang-gao-jian-ce-zhong-de-xin-deng-lu-wei-shi-mo-he-dan-tu-li-mian-de-xin-deng-lu-yong-hu-lia" id="3-zai-guang-gao-jian-ce-zhong-de-xin-deng-lu-wei-shi-mo-he-dan-tu-li-mian-de-xin-deng-lu-yong-hu-lia"></a>

* 广告监测的新登录是按照点击然后激活的时间戳统计，单图里面的新登录以新登录的时间戳统计。
* 广告监测的新登录会根据设备去重，单图里面的新登录不根据设备去重。

### **4. Web的广告监测为什么没有新访问用户和访问用户的数据？** <a href="#4-web-de-guang-gao-jian-ce-wei-shi-mo-mei-you-xin-fang-wen-yong-hu-he-fang-wen-yong-hu-de-shu-ju" id="4-web-de-guang-gao-jian-ce-wei-shi-mo-mei-you-xin-fang-wen-yong-hu-he-fang-wen-yong-hu-de-shu-ju"></a>

检查一下该落地页有没有集成我们的SDK，以及目标链接填写是否正确。

### **5. web的广告监测链接为什么没有统计到点击数？** <a href="#5-web-de-guang-gao-jian-ce-lian-jie-wei-shi-mo-mei-you-tong-ji-dao-dian-ji-shu" id="5-web-de-guang-gao-jian-ce-lian-jie-wei-shi-mo-mei-you-tong-ji-dao-dian-ji-shu"></a>

* 明确是否使用我们这边生成的监测链接去投放。
* 链接是否被压缩成了 t.cn 的格式，目前链接不支持t.cn的压缩。

### **6. App的广告监测为什么没有激活？** <a href="#6-app-de-guang-gao-jian-ce-wei-shi-mo-mei-you-ji-huo" id="6-app-de-guang-gao-jian-ce-wei-shi-mo-mei-you-ji-huo"></a>

请检查一下您投放的应用包名和在GIO平台填写的应用包名是否一致，我们的监测链接根据包名生成，如不一致，请您在我们的平台修改包名重新创建链接后再进行投放。

### **7. 推广详细里面点击率为什么是NaN%？** <a href="#7-tui-guang-xiang-xi-li-mian-dian-ji-shuai-wei-shi-mo-shi-nan" id="7-tui-guang-xiang-xi-li-mian-dian-ji-shuai-wei-shi-mo-shi-nan"></a>

点击率的计算逻辑是 去重点击/展现，展现没有数据时点击率会出现NaN%。

### **8. 为什么 GrowingIO 的短链接无法在小米手机中被识别为链接样式？** <a href="#8-wei-shi-mo-growingio-de-duan-lian-jie-wu-fa-zai-xiao-mi-shou-ji-zhong-bei-shi-bie-wei-lian-jie-yan" id="8-wei-shi-mo-growingio-de-duan-lian-jie-wu-fa-zai-xiao-mi-shou-ji-zhong-bei-shi-bie-wei-lian-jie-yan"></a>

目前小米手机 MIUI 系统最新版本中，对某些 URL 链接识别存在误判，导致对 URL 识别为文本，而不能识别为链接，该误判情况不仅限于 GrowingIO 短链接。对于该情况，GrowingIO 提以下备选方案：

* 使用 GrowingIO 备用域名 t.growingio.com 代替 datayi.cn ，替换后即可正常识别。例如短链为：https://datayi.cn/x1234，替换后为：https://t.growingio.com/x1234。
* 使用域名映射服务，将 GrowingIO 短链映射为自己的域名，直接投放映射后的域名，详细配置参考默认渠道来源跟踪 > [公司域名与GrowingIO短链建立映射关系](othe-info/default-channel-tracking.md)。

域名升级

为避免监测链接被部分移动设备拦截，GrowingIO 监测链接域名已由 gio.ren 升级为 datayi.cn ，此前已有链接不受升级影响，使用新域名需先完成域名升级配置，相关配置请参考[DeepLink启用新域名](https://growingio.gitbook.io/docs/product-manual/growing/ads/info/newdomain)。
