---
title: CA3147:ValidateAntiForgeryToken で動詞ハンドラーをマークします
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 96660dfe1de6b4fb2490bd00b7ce408d0548ba67
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954699"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147:ValidateAntiForgeryToken で動詞ハンドラーをマークします

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

ASP.NET MVC コント ローラー アクション メソッドが付いていない[ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118))、またはなど、HTTP 動詞を指定する属性[HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118))または[AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29)します。

## <a name="rule-description"></a>規則の説明

ASP.NET MVC のコント ローラーを設計するときは、クロスサイト リクエスト フォージェリ攻撃考慮あります。 クロスサイト リクエスト フォージェリ攻撃対象は、ASP.NET MVC コント ローラーに、認証されたユーザーから悪意のある要求を送信できます。 詳細については、次を参照してください。 [ASP.NET MVC と web ページの XSRF/CSRF 防止](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages)します。

このルールは、その ASP.NET MVC コント ローラーを確認します。 アクション メソッドか。

- [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29)し、HTTP GET を含まない、許可されている HTTP 動詞を指定します。

- HTTP GET を許可されている動詞として指定します。

## <a name="how-to-fix-violations"></a>違反の修正方法

- ASP.NET MVC コント ローラー アクションを HTTP GET 要求を処理し、有害な可能性のある副作用はありません、追加、 [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29)メソッドにします。

   HTTP GET を処理するコント ローラー アクションが要求し、有害な可能性のある副作用が伴う機密データの変更など、ASP.NET MVC があれば、アプリケーションがクロスサイト リクエスト フォージェリ攻撃に対して脆弱になります。  HTTP POST、PUT、または DELETE 要求だけが機密性の高い操作を実行するために、アプリケーションを再設計する必要があります。

- HTTP POST を処理するコント ローラー アクションの ASP.NET MVC、PUT、または削除を要求する追加[ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118))と使用できる HTTP 動詞を指定する属性 ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29)、 [HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29)、 [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29)、または[HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29))。 さらを呼び出す必要があります、 [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) MVC ビューまたは Razor web ページからのメソッド。 例については、次を参照してください。[編集メソッドを調べると、ビューの編集](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view)します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

場合、この規則による警告を抑制しても安全です。

- ASP.NET MVC のコント ローラー アクションには、有害な副作用はありません。

- アプリケーションでは、別の方法で偽造防止トークンを検証します。

## <a name="validateantiforgerytoken-attribute-example"></a>ValidateAntiForgeryToken 属性の例

### <a name="violation"></a>違反

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>HttpGet 属性の例

### <a name="violation"></a>違反

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
