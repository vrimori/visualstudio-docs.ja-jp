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
ms.openlocfilehash: 103000c2ded944236762ffd55603877ece7b7968
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809467"
---
次の手順では、IIS の基本構成のみを表示します。 詳細については、または Windows デスクトップ マシンにインストールするを参照してください。 [IIS への発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)または[IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

Windows Server オペレーティング システムでは、使用、**追加の役割と機能の**ウィザードを使用して、**管理**リンクまたは**ダッシュ ボード**リンク**サーバー マネージャー**. **[サーバーの役割]** のステップで、**[Web サーバー (IIS)]** チェック ボックスをオンにします。

![[サーバーの役割の選択] のステップで Web サーバー IIS の役割を選択します。](../media/remotedbg-server-roles-ws2012.png)

**[役割サービス]** のステップで、希望する IIS の役割サービスを選択するか、既定の役割サービスをそのまま使用します。 使用して展開を有効にする場合は、発行設定と Web Deploy、ことを確認します**IIS 管理スクリプトおよびツール**が選択されています。

Web サーバーの役割とサービスをインストールする確認の手順を実行します。 Web サーバー (IIS) の役割をインストールした後、サーバーと IIS の再起動は必要ありません。