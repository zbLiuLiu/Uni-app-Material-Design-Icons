# mdi-icon

本插件为非官方插件，原作者为 [Pictogrammers](//pictogrammers.com/ "Pictogrammers") 。由于插件作者常年使用[Vuetify.js](//vuetifyjs.com "Vuetify.js")框架进行前端开发，发现该框架使用的[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")图标库资源丰富拥有7000+图标、风格基本统一、还很易用，后来迁移到uni-app进行小程序开发时一直苦于没有找到跟[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")比拟的图标库（尽管[阿里巴巴图标矢量库](//www.iconfont.cn/ "阿里巴巴图标矢量库")等图标库资源远比该库丰富，但里面有着大量样式或使用场景重复或相似的图标），故自己将其移植过来了。

**⚠️特别提醒：**该仓库使用了官方部署在jsDelivr上的字体，不建议在生产环境使用！！！[查看关于字体文件的问题](#1. 关于字体文件的问题 "查看关于字体文件的问题")


------------

@[toc](目录)

------------

## 快速上手

本插件包含一个`mdi-icon`组件，您可以在页面的任何位置使用该组件。

### 组件属性

| 属性名称 | 类型 | 限制范围 | 是否必填 | 描述 |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| `icon` | `string` | [Material Design Icons](//materialdesignicons.com/ "Material Design Icons")里的图标 | 是 | 图标名称，您可以在[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")里寻找合适的图标并找到其对应的图标名称。<br/>**特别强调的是：**由于[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")里的图标信息始终为最新版的，可能会与您当前使用的版本不符，如果不符则会出现无法显示新版本中新增的图标的问题，详细内容见[下文](#2. 旧版本插件无法显示新版本图标库中新增的图标的问题 "下文")。 |
| `rotate` | `string` &verbar; `number` | `[ 45, 90, 135, 180, 225, 270, 315 ]` | 否 | 图标旋转角度，不填则不旋转。 |
| `flip` | `string` | `["horizontal","vertical"]` | 否 | 图标翻转方向，不填则不翻转。 |

------------

## 使用方法

没怎么用过uni-app，光看开发文档也没看明白，也不知道我搞得对不对。但好像可以用`easycom`自动引入，或者点点插件详情页右侧的
<a class="btn btn-hx-import hmt-btn-hx-import" onclick="download_plugin(1, 0)" href="javascript:void(0)" data-loading-text="<span class='glyphicon-left glyphicon glyphicon-refresh spinning'></span>处理中..."><img src="//img-cdn-aliyun.dcloud.net.cn/dev/img/ext/hx2@2x.png">  使用 HBuilderX 导入插件</a>
试试？

------------

## 关于issue和PR

如果您对图标有好的建议或想法，欢迎前往[官方的Github仓库](//github.com/Templarian/MaterialDesign "官方的Github仓库")提出，请在提出issue或者pr前仔细阅读官方的[README](//github.com/Templarian/MaterialDesign/blob/master/README.md "README")（英文），不阅读文档直接提issue或者PR是非常不礼貌的行为。

如果您在使用本插件时遇到了问题或有什么好的建议，请直接在评论区留言或前往[本插件的仓库](//github.com/zbLiuLiu/Uni-app-Material-Design-Icons "本插件的仓库")提交issue或PR。请不要到官方的Github仓库发布关于本插件的issue或pr，本插件为非官方插件，官方不维护本插件，插件作者也不会闲着没事去官方的Github仓库寻找关于插件的issue或PR……（特别是PR！！！）

------------

## 图标库更新

插件作者尽量保证本插件与官方最新版图标库同步，但由于个人时间精力有限，可能无法及时更新或跳过一些版本。欢迎有志之士一同维护本插件。

如果您需要自行更新图标库，本项目中包含了一个修改版的[MaterialDesign-Webfont](//github.com/Templarian/MaterialDesign-Webfont "MaterialDesign-Webfont")项目，项目位于`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont`，如果DCloud官方未将Git相关的内容删除的话，您可以直接从该项目里将最新版的[MaterialDesign-Webfont](//github.com/Templarian/MaterialDesign-Webfont "MaterialDesign-Webfont")拉取下来并合并（只保留本项目中`MaterialDesign-Webfont/scss/_variables.scss`的第10行`$mdi-font-path`变量，其它内容不保留，否则图标将不可用）。

**⚠️特别提醒：**如果您对`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont`里的内容还做出了其它修改，请记得一并保留。

**⚠️特别提醒+1：**如果Git相关的内容被删除了，您也可以重新在`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont`创建Git，但请保留`MaterialDesign-Webfont/scss/_variables.scss`的第10行`$mdi-font-path`变量。

------------

## 其它问题

### 1. 关于字体文件的问题

由于小程序不支持使用本地字体，且为了保持本插件使用的图标库与官方最新版图标库版本，不适用将字体文件编码成Base64格式文本包含在样式表文件中，插件作者亦没钱自己搞公共服务器。因此本插件使用了官方部署在jsDelivr上的字体，jsDelivr在大陆的访问速度尚可，但考虑到项目风险，建议有风控需求的项目将字体文件自行部署到自有服务器上。

**⚠️特别提醒：**当您对`@/uni_modules/`文件夹里的插件做出修改时，您应当确保不再更新被修改过的插件，否则您做出的修改可能会被覆盖掉！

#### 将字体文件部署到自有服务器

字体文件存放在`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/fonts`文件夹中，与您所使用的插件版本对应，将该目录下的所有文件部署到自有服务器的同一目录即可。

#### 使用自有服务器上的字体文件

将`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/scss/_variables.scss`第10行的`$mdi-font-path`变量修改为您部署在自有服务器上的字体文件URL所在的目录。**目录不要以`/`结尾！**

例如：您部署在自有服务器上的四个字体文件的URL分别是：
- `//example.com/my-font/materialdesignicons-webfont.eot`
- `//example.com/my-font/materialdesignicons-webfont.ttf`
- `//example.com/my-font/materialdesignicons-webfont.woff`
- `//example.com/my-font/materialdesignicons-webfont.woff2`

那么您需要将`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/scss/_variables.scss`第10行的`$mdi-font-path`变量修改为`//example.com/my-font`。

#### 自行将字体文件编码成Base64格式文本包含在样式表文件中

您可以将`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/fonts`文件夹中的文件分别编码成Base64格式文本，并将其添加到`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/scss/_path.scss`的对应位置。

**⚠️特别提醒：**当您将自行将字体文件编码成Base64格式文本包含在样式表文件中后，图标库将无法被更新。不过您可以自行通过官方仓库获取到新版图标库的字体文件并将其重新编码成Base64格式文本包含在样式表文件中，并将官方仓库[MaterialDesign-Webfont](//github.com/zbLiuLiu/Uni-app-Material-Design-Icons "MaterialDesign-Webfont")的`/scss/_variables.scss`文件中的`$mdi-icons`变量覆盖到`@/uni_modules/mdi-icon/components/mdi-icon/MaterialDesign-Webfont/scss/_variables.scss`文件中的`$mdi-icons`变量。

### 2. 旧版本插件无法显示新版本图标库中新增的图标的问题

插件版本与图标库版本是对应的，而[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")里的图标库永远是最新的，如果您在[Material Design Icons](//materialdesignicons.com/ "Material Design Icons")里寻找到了一个中意的图标，并将其使用在了项目中，却发现在字体文件加载完成后仍然无法显示，那么您可能恰好用了一个新版图标库中新增的图标。

这是一个非常容易理解的问题，更新插件（如果有新版本）或者按照上文“[图标库更新](#图标库更新 "图标库更新")”里的方式更新图标库即可。

------------

## 版权信息

本插件中包含的[Material Design Icons](://materialdesignicons.com/ "Material Design Icons")部分遵循[Pictogrammers Free License](//github.com/Templarian/MaterialDesign-Webfont/blob/master/LICENSE "Pictogrammers Free License")协议，该协议表示：这个图标集由 [Pictogrammers](//pictogrammers.com/ "Pictogrammers") 提供，是免费的、开源的，并且对 GPL 友好。您可以在商业项目、开源项目或其它任何项目中使用它。

本插件的`mdi-icon`组件部分遵循[MIT](//opensource.org/licenses/MIT "MIT")协议，该组件遵循[MIT](//opensource.org/licenses/MIT "MIT")协议表示：这个组件是免费的、开源的。您可以在商业项目、开源项目或其它任何项目中使用它。

本插件的示例部分遵循[GPL-2.0](//opensource.org/licenses/GPL-2.0 "GPL-2.0")协议，示例部分遵循[GPL-2.0](//opensource.org/licenses/GPL-2.0 "GPL-2.0")协议表示：示例部分是开源的。您复制、使用、修改示例部分的项目必须同样遵循GPL协议进行开源。

**⚠️特别注明：**本插件的示例部分是免费的。本插件的`mdi-icon`组件部分不算做示例，您可以自由使用它。只要您的项目未使用到本插件的示例部分，您就不受[GPL-2.0](//opensource.org/licenses/GPL-2.0 "GPL-2.0")协议的约束。