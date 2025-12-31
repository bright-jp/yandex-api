# Yandex Search Scraper

[![Promo](https://media.brightdata.com/2025/08/SERP-API-50-off-GitHub-banner_1389_166.png)](https://brightdata.jp/products/serp-api/yandex-search)

このリポジトリでは、Yandex 検索エンジン結果ページ（SERP）からデータを抽出するための、信頼性の高い2つのソリューションを提供しています。

- **無料の Yandex Scraper:** 小規模で Yandex 検索結果をスクレイピングするための基本ツールです
- **エンタープライズグレードの Yandex SERP API:** 大量・リアルタイムのデータ抽出に対応した、スケーラブルで本番運用可能なソリューションです（[Bright Data の SERP Scraper API](https://brightdata.jp/products/serp-api) の一部です）

## Table of Contents
- [Free Yandex SERP Scraper](#free-yandex-serp-scraper)
  - [Setup Requirements](#setup-requirements)
  - [Quick Start Guide](#quick-start-guide)
  - [Sample Output](#sample-output)
  - [Limitations](#limitations)
- [Yandex SERP Scraper API](#yandex-serp-scraper-api)
  - [Key Benefits](#key-benefits)
  - [Getting Started](#getting-started)
- [Implementation Methods](#implementation-methods)
  - [Direct API Access](#direct-api-access)
  - [Native Proxy-Based Access](#native-proxy-based-access)
- [Yandex Search Query Parameters](#yandex-search-query-parameters)
  - [Localization](#localization)
  - [Pagination](#pagination)
  - [Time Range](#time-range)
  - [Device Targeting](#device-targeting)
- [Practical Example](#practical-example)
- [Support & Resources](#support--resources)

## Free Yandex SERP Scraper

無料のスクレイパーは、小規模で Yandex SERP データを収集するための分かりやすい方法を提供します。個人プロジェクト、研究、またはテスト目的で限定的なデータが必要な開発者に最適です。

<img width="800" alt="free-yandex-serp-scraper" src="https://github.com/luminati-io/yandex-api/blob/main/images/428371413-775c71f6-10cf-4a2d-91b8-6f137db5b171.png" />

### Setup Requirements

- [Python 3.9+](https://www.python.org/downloads/)
- 必要なパッケージ:
    - ブラウザ自動化のための `playwright`
    - HTML 解析のための `BeautifulSoup`

```bash
pip install playwright beautifulsoup4
playwright install
```

> **Webスクレイピングが初めてですか？** こちらの [Beginner's Guide to Web Scraping with Python](https://brightdata.jp/blog/how-tos/web-scraping-with-python) をご覧ください
>

### Quick Start Guide

1. [yandex-search-results-scraper.py](https://github.com/luminati-io/yandex-api/blob/main/yandex-serp-scraper/yandex-serp-scraper.py) を開きます
2. 検索語とページ数の変数をカスタマイズします:

```python
PAGES_PER_TERM = {
    "ergonomic office chair": 2,
}
```

3. スクリプトを実行します

### Sample Output
<img width="800" alt="yandex-scraper-output" src="https://github.com/luminati-io/yandex-api/blob/main/images/428371812-dbd6f456-af64-4a4a-8735-f26876ae5fa8.png" />


### Limitations
Yandex をスクレイピングする際の最大の課題の1つは、攻撃的な CAPTCHA 保護です:

<img width="800" alt="yandex-captcha-challenge" src="https://github.com/luminati-io/yandex-api/blob/main/images/428371880-309e645f-c043-4231-aeb2-c3417e91b15e.png" />


Yandex は、自動データ抽出を防ぐために、厳格かつ継続的に進化するアンチボットシステムを使用しています。CAPTCHA が頻繁に発生すると、すぐに IP ブロックにつながり、安定して長時間稼働するスクレイパーの維持が困難になります。

無料スクレイパーは基本的なタスクには対応しますが、いくつか重要な制限があります:

- IP ブロックの高いリスク
- リクエスト量の制限
- CAPTCHA による継続的な中断
- 本番環境には不適

スケーラブルで安定したソリューションとして、以下で詳述する Bright Data の専用 API をご検討ください。 👇


## Yandex SERP Scraper API

[Yandex Search API](https://brightdata.jp/products/serp-api/yandex-search) は、Bright Data の [SERP Scraping API](https://brightdata.jp/products/serp-api) スイートの一部です。業界をリードする [proxy infrastructure](https://brightdata.jp/proxy-types) を活用し、単一の API 呼び出しでリアルタイムの Yandex 検索結果を提供します。

### Key Benefits

- **グローバルな精度**: 世界中の特定の場所向けに最適化された結果を取得できます
- **Pay-Per-Success**: 成功したリクエストに対してのみ課金されます
- **リアルタイムデータ**: 最新の検索結果に数秒でアクセスできます
- **無制限のスケーラビリティ**: 大量のスクレイピングを容易に処理できます
- **コスト効率**: 高額なインフラが不要になります
- **信頼性の高いパフォーマンス**: アンチブロッキング技術を内蔵しています
- **24/7 の専門サポート**: 必要なときにいつでも技術支援を利用できます

 📌 Try Before You Buy: Test it for free in our SERP API Live Demo
 
 <img width="800" alt="bright-data-serp-api-playground" src="https://github.com/luminati-io/yandex-api/blob/main/images/428391143-c089343e-50a8-4961-8d11-d312982480df.png" />


### Getting Started

1. [Bright Data アカウントを作成](https://brightdata.jp/) します（新規ユーザーには $5 のクレジットが付与されます）
2. [API key](https://docs.brightdata.com/general/account/api-token) を生成します
3. [step-by-step guide](https://github.com/luminati-io/yandex-api/blob/main/setup-serp-api-guide.md) に従って SERP API を構成します


## Implementation Methods

### Direct API Access

API を使用する最も簡単な方法は、Bright Data の API endpoint へ直接リクエストを送信することです。

**cURL Example:**

```bash
curl https://api.brightdata.com/request \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d '{
        "zone": "ZONE_NAME",
        "url": "https://www.yandex.com/search/?text=apple+watch+series+10+review&lr=95&lang=en",
        "format": "raw"
      }'
```

**Python Example:**

```python
import requests
import json

url = "https://api.brightdata.com/request"

headers = {"Content-Type": "application/json", "Authorization": "Bearer API_TOKEN"}

payload = {
    "zone": "ZONE_NAME",
    "url": "https://www.yandex.com/search/?text=apple+watch+series+10+review&lr=95&lang=en",
    "format": "raw",
}

response = requests.post(url, headers=headers, json=payload)

with open("yandex-scraper-api-result.html", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved!")
```

### Native Proxy-Based Access

この代替方法では、検索結果へ直接アクセスするためにプロキシルーティングを使用します。

**cURL Example:**

```bash
curl -i \
  --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<CUSTOMER_ID>-zone-<ZONE_NAME>:<ZONE_PASSWORD> \
  -k \
  "https://www.yandex.com/search/?text=apple+watch+series+10+review&lr=95&lang=en"
```

**Python Example:**

```python
import requests
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

host = "brd.superproxy.io"
port = 33335
username = "brd-customer-<customer_id>-zone-<zone_name>"
password = "<zone_password>"
proxy_url = f"http://{username}:{password}@{host}:{port}"

proxies = {"http": proxy_url, "https": proxy_url}

url = "https://www.yandex.com/search/?text=apple+watch+series+10+review&lr=95&lang=en"
response = requests.get(url, proxies=proxies, verify=False)

with open("yandex-scraper-api-result.html", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved!")
```

> **Note:** ネイティブプロキシ方式を使用する場合は、本番利用のために Bright Data の SSL 証明書をインストールすることを推奨します。詳細は [SSL Certificate Guide](https://docs.brightdata.com/general/account/ssl-certificate) をご覧ください。
> 

👉 [full HTML output](https://github.com/luminati-io/yandex-api/blob/main/yandex-scraper-api-output/yandex-scraper-api-result.html) をご覧ください

*`lr` や `lang` のようなクエリパラメータは次のセクションで説明します。*


## Yandex Search Query Parameters

### Localization

#### Region (`lr`)

このパラメータは、検索結果の対象とする地理的な地域または国を定義します。

| Region | Code |
| --- | --- |
| Moscow | 1 |
| Saint-Petersburg | 2 |
| USA | 84 |
| Canada | 95 |
| China | 134 |

Example - "best wireless earbuds" が USA でどのようにランクされるかを確認します:

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user brd-customer-<id>-zone-<zone>:<password> \
     "https://www.yandex.com/search/?text=best+wireless+earbuds&lr=84"
```

#### Language (`lang`)

2文字の言語コードを使用して、言語の優先設定を指定します:

- `lang=en` - 英語
- `lang=es` - スペイン語
- `lang=fr` - フランス語

Example - スペイン語でスポーツニュースを取得します:

```bash
https://www.yandex.com/search/?text=local+sports+news&lang=es
```

### Pagination

#### Page Number (`p`)

表示する結果ページを制御します:

- `p=0` - 1ページ目（デフォルト）
- `p=1` - 2ページ目
- `p=4` - 5ページ目

各 Yandex SERP ページは通常 10 件の結果を返します。

Example - "nike running shoes" で3ページ目（結果 21-30）をスクレイピングします:

```bash
https://www.yandex.com/search/?text=nike+running+shoes&p=2
```

### Time Range

#### Time Period (`within`)

結果を特定の期間に限定します:

- `within=77` - 過去 24 時間の結果
- `within=1` - 過去 2 週間の結果
- `within=[%pm]` - 過去 1 か月の結果

Example - 過去 24 時間の "iPhone 15 review" の結果を取得します:

```bash
https://www.yandex.com/search/?text=iphone+15+review&within=77
```

### Device Targeting

#### Device Type (`brd_mobile`)

シミュレートするデバイスタイプを指定します:

- `brd_mobile=0` または省略 - ランダムなデスクトップ user-agent
- `brd_mobile=1` - ランダムなモバイル user-agent
- `brd_mobile=ios` または `brd_mobile=iphone` - iPhone user-agent
- `brd_mobile=ipad` または `brd_mobile=ios_tablet` - iPad user-agent
- `brd_mobile=android` - Android phone user-agent
- `brd_mobile=android_tablet` - Android tablet user-agent

Example - レスポンシブ Web サイトのテストを iPhone で検索している状況をシミュレートします:

```bash
https://www.yandex.com/search/?text=responsive+website+testing&brd_mobile=ios
```

#### Browser Type (`brd_browser`)

シミュレートするブラウザを定義します:

- Default (omitted) - ランダムなブラウザ
- `brd_browser=chrome` - Google Chrome
- `brd_browser=safari` - Safari
- `brd_browser=firefox` - Mozilla Firefox

Example - Python チュートリアルを検索する Safari ブラウザをシミュレートします:

```bash
https://www.yandex.com/search/?text=how+to+learn+python&brd_browser=safari
```

> **Note:** `brd_browser=firefox` と `brd_mobile=1` は互換性がないため、組み合わせないでください。
> 

## **Practical Example**

包括的なターゲティングのために、複数のパラメータを組み合わせることができます:

```bash
https://www.yandex.com/search/?text=organic+skincare+products
&lr=95
&lang=en
&p=2
&within=1
&brd_mobile=ios
&brd_browser=safari
```

この検索は次を行います:

- カナダのユーザーを対象にします（`lr=95`）
- 英語の結果を表示します（`lang=en`）
- 2ページ目を表示します（`p=2`）
- 過去 2 週間に限定します（`within=1`）
- iPhone ユーザーをシミュレートします（`brd_mobile=ios`）
- Safari ブラウザを使用します（`brd_browser=safari`）

カナダ市場における最近のオーガニックスキンケア製品トレンドを、iOS モバイルユーザーが閲覧する視点で調査したいスキンケア企業に最適です。


## Support & Resources

- **Documentation:** [SERP API Documentation](https://docs.brightdata.com/scraping-automation/serp-api/)
- **Related APIs:**
    - [SERP API](https://github.com/luminati-io/serp-api)
    - [Google Search API](https://github.com/luminati-io/google-search-api)
    - [Google News Scraper](https://github.com/luminati-io/Google-News-Scraper)
    - [Google Trends API](https://github.com/luminati-io/google-trends-api)
    - [Google Reviews API](https://github.com/luminati-io/google-reviews-api)
    - [Google Hotels API](https://github.com/luminati-io/google-hotels-api)
    - [Google Flights API](https://github.com/luminati-io/google-flights-api)
    - [Web Unlocker API](https://github.com/luminati-io/web-unlocker-api)
- **Use Cases:**
    - [SEO & SERP Tracking](https://brightdata.jp/use-cases/serp-tracking)
    - [Travel Industry Data](https://brightdata.jp/use-cases/travel)
- **Additional Reading:** [Best SERP APIs](https://brightdata.jp/blog/web-data/best-serp-apis)
- **Contact Support:** [support@brightdata.com](mailto:support@brightdata.com)