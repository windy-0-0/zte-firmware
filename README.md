# zte-firmware

中兴 ZTE 7552N（畅行60 / P720S20）官方固件 **HCTSW_ZTE_7552N_13.0.18CN**

## 内容

| 文件 | 说明 | 原始大小 |
|---|---|---|
| `HCTSW_ZTE_7552N_13.0.18CN.pac` | 展锐线刷 PAC 包（解压自 .7z） | 6,587,280,721 字节（6.58 GB） |
| `HCTSW_ZTE_7552N_13.0.18CN.pac.7z` | 官方原版压缩包 | 4.71 GB |

固件来源：HCT_Nekobot（HikariCalyx 刷机团队）。13.0.18 最终版，不含任何修改。

## ⚠️ 分片下载与还原

GitHub Release 单文件上限 2GB，因此固件以 **tar.gz 流 + 200MB 分片** 形式上传。

### 还原步骤

```bash
# 1. 下载全部分片（务必用通配符下载同一组）
gh release download v1.0 -R windy-0-0/zte-firmware -p "zte-pac-part-*"

# 2. 按字典序合并分片并解压（split 默认按 aa..zz 排序，ls 的字典序即为正确顺序）
cat zte-pac-part-* | tar xzf -

# 3. 校验（关键！）
shasum -a 256 HCTSW_ZTE_7552N_13.0.18CN.pac
# 期望: c73cc25d50a83d15bb7147970a1a69875bcd7c8e52c236c8b1af4208411b34f8
```

### 分片清单

| 组 | 分片前缀 | 片数 | 流总字节 |
|---|---|---|---|
| PAC 包 | `zte-pac-part-aa` … `zte-pac-part-bc` | 29 | 5,888,378,880 |
| 7z 原包 | `zte-7z-part-aa` … `zte-7z-part-ay` | 25 | 5,054,279,680 |

> 前 28 片各 200MB（209,715,200 字节），末片为余数。片数与总字节数是完整性的第一道校验。

## 刷机说明

1. 解压 `.pac` 文件
2. 用展锐 **ResearchDownload** 工具加载 PAC 包
3. 手机进 download 模式（音量下 + 电源），工具自动识别
4. 整包线刷，可修复 boot / vbmeta 等所有分区

详见 `zte-rescue-kit` 仓库中的 `00-操作SOP-按顺序执行.md` 与 `救砖操作手册.md`。

## 其他资源

- 123 云盘原始链接：https://www.123865.com/s/wnu3jv-sNg6d?pwd=vEXR （提取码 `vEXR`）
- 萤火虫资源站畅行60目录：https://www.yhcres.top/02-手机平板/中兴ZTE/畅行 60
