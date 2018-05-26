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
ms.openlocfilehash: 62bdcd8109263cc86e13484d146e46f8e95c7198
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
次の手順では、IIS の基本的な構成のみを表示します。 詳細な情報や Windows デスクトップ コンピューターにインストールする場合を参照してください。[を IIS に発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)または[IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

Windows Server オペレーティング システムを使用して、**追加の役割と機能の**ウィザードを使用して、**管理**リンクまたは**ダッシュ ボード**でリンク**サーバー マネージャー**. **[サーバーの役割]** のステップで、**[Web サーバー (IIS)]** チェック ボックスをオンにします。

![[サーバーの役割の選択] のステップで Web サーバー IIS の役割を選択します。](../media/remotedbg-server-roles-ws2012.png)

**[役割サービス]** のステップで、希望する IIS の役割サービスを選択するか、既定の役割サービスをそのまま使用します。 Web Deploy を使用して展開する場合、以下のことを確認**IIS 管理スクリプトおよびツール**が選択されています。

Web サーバーの役割とサービスをインストールする確認の手順を実行します。 Web サーバー (IIS) の役割をインストールした後、サーバーと IIS の再起動は必要ありません。