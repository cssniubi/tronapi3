# 🌍 [English Doc](./README.en.md) | 🚀 TronApi3🔥🔥🔥

**TronApi3** 是一个开发团队的精心之作，专为当前最热门的波场生态打造。我们为您提供了完整的波场API对接方案，助力小白快速实现区块链开发，轻松上手！

如果你正在给老板夸下海口，或者需要开发支持，不妨与我聊聊！我或许能帮你解决大问题。  
⚡ **无后门、无加密**，代码简洁易懂，基于 **ThinkPHP** 编写，轻松二次开发，支持部署成独立API供内部调用。

我能帮你快速完成波场开发，避开常见的坑，解答所有相关问题，让你的开发项目轻松起飞！🌍

🌟 TronApi3 让区块链开发变得轻松！我们帮助你避开所有坑，让开发更顺畅，让你从零到一轻松实现项目！🚀

🔊 承接所有编程语言的开发需求，不限于Python，Golang，PHP，Java等 💓

---

## 🌐 重要链接

- **测试地址**: [测试API](https://trx.phpcode.site/)
- **在线文档**: [TronApi3 文档](https://tronapi.gitbook.io/trx)
- **项目官网**: [TronApi3 官网](https://www.phpcode.site/)

---

## 📈 我们的能力

如果你是 **老板** 👔，没有开发团队，别担心！我们可以承担您的所有开发需求。自 **2020年** 至今，我们已经承接了多个国际超大项目，单个项目流水超过 **100,000,000 USDT** 🌟。

### 主要优势：
- **高效开发**，不拖后腿
- **强大运营能力**，项目落地多国
- **多语言支持**，后期可脱离开发自运营
- **全程高质量服务**，您完全可以放心交给我们

---

## 📦 项目概述

**TronApi3** 是一款简洁易懂、功能丰富的波场区块链API接口，支持以下核心功能：
- 生成钱包 🏦
- **USDT 转账** 💸
- **TRX 转账** 🔄
- 查询余额 💰
- **私钥转地址** 🔑➡️📍

所有 API 都支持 **GET 请求**，如果需要更高的安全性，可以通过 **POST 请求**。  
这个项目不仅适合新手学习区块链原理，也能支持一些简单的开发需求。

---

## 💻 技术架构

**TronApi3** 基于 **ThinkPHP 5** 框架开发，代码简洁，易于理解与修改。您可以快速上手，进行二次开发或根据需求部署成 API 服务。

---

## 🛠 安装教程

1. **PHP 7.3 或 7.4** 环境
2. 必须安装 **GMP 扩展**（否则转账会失败）
3. 配置 **伪静态**
4. 运行目录设置为 `public` 文件夹
5. 合约地址无需更改
6. 配置好后，关闭调试模式，确保安全

---

## 🔑 API Key 配置

如果你需要提升API调用的量，建议申请 **API Key** 以避免限制。  
[申请 API Key](https://www.trongrid.io/)

### 配置步骤：

1. 打开文件 `vendor/fenguoz/tron-php/src/Api.php`
2. 替换 `post` 方法如下：

```php
/**
 * 用于处理常见功能，如格式化POST数据和错误处理
 *
 * @throws TronErrorException
 */
public function post(string $endpoint, array $data = [], bool $returnAssoc = false)
{
    if (sizeof($data)) {
        $data = [
            'headers' => [
                'TRON-PRO-API-KEY' => 'your api key'  // 填入您的API Key
            ],
            'json' => $data
        ];
    }
    $stream = (string)$this->getClient()->post($endpoint, $data)->getBody();
    $body = json_decode($stream, $returnAssoc);
    $this->checkForErrorResponse($returnAssoc, $body);
    return $body;
}
```
## 📞 联系方式
获取支持或购买源码，欢迎联系：

Telegram: 🍭🍭🍭 [@king_orz](https://t.me/king_orz)




## Install

```bash
> composer require iexbase/tron-api --ignore-platform-reqs
```
## Requirements

The following versions of PHP are supported by this version.

* PHP 7.4

## Example Usage

```php
use IEXBase\TronAPI\Tron;

$fullNode = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');
$solidityNode = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');
$eventServer = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');

try {
    $tron = new \IEXBase\TronAPI\Tron($fullNode, $solidityNode, $eventServer);
} catch (\IEXBase\TronAPI\Exception\TronException $e) {
    exit($e->getMessage());
}


$this->setAddress('..');
//Balance
$tron->getBalance(null, true);

// Transfer Trx
var_dump($tron->send('to', 1.5));

//Generate Address
var_dump($tron->createAccount());

//Get Last Blocks
var_dump($tron->getLatestBlocks(2));

//Change account name (only once)
var_dump($tron->changeAccountName('address', 'NewName'));


// Contract
$tron->contract('Contract Address');



```

## Testing

``` bash
$ vendor/bin/phpunit
```
