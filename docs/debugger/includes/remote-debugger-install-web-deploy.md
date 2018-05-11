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
ms.openlocfilehash: c22ba73b464f91bf3036541304cdf94e8660970d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
1. Visual Studio での Web 配置でアプリケーションを配置する場合は、サーバーで Web Deploy の最新バージョンをインストールします。

    Web Deploy をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)です。 (を IIS から Web Platform Installer のリンクを検索する  **IIS**サーバー マネージャーの左側のウィンドウでします。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**)。

    Web Platform Installer で、アプリケーション タブで、Web Deploy を検索します。直接インストーラーを入手することも、 [Microsoft ダウンロード センター](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)です。 

2. Web Deploy が実行される確認正しく開くことによって**コントロール パネル > システムとセキュリティ > 管理ツール > サービス**ことを確認および**Web Deployment Agent サービス**が実行されている (サービス名は旧バージョンでは異なる) です。

    エージェント サービスが実行されていない場合は、それを開始します。 これが存在しない場合を参照してください。**コントロール パネル > プログラム > プログラムのアンインストール**、検索**Microsoft Web Deploy <version>** です。 選択**変更**インストールを選択することを確認し、**はローカル ハード ドライブにインストールする**Web 配置のコンポーネントです。 変更のインストール手順を完了します。