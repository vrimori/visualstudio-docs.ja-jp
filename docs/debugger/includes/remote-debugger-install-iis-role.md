---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 103cefa8573c8f44efff0b53b0c09a5ec26706e6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
次の手順では、IIS の基本的な構成のみを表示します。 詳細な情報や Windows デスクトップ コンピューターにインストールする場合を参照してください。[を IIS に発行](https://docs.microsoft.com/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)または[IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

Windows Server オペレーティング システムを使用して、**追加の役割と機能の**ウィザードを使用して、**管理**リンクまたは**ダッシュ ボード**でリンク**サーバー マネージャー**. **[サーバーの役割]** のステップで、**[Web サーバー (IIS)]** チェック ボックスをオンにします。

![[サーバーの役割の選択] のステップで Web サーバー IIS の役割を選択します。](../media/remotedbg-server-roles-ws2012.png)

**[役割サービス]** のステップで、希望する IIS の役割サービスを選択するか、既定の役割サービスをそのまま使用します。

Web サーバーの役割とサービスをインストールする確認の手順を実行します。 Web サーバー (IIS) の役割をインストールした後、サーバーと IIS の再起動は必要ありません。