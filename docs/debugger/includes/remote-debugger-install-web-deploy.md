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
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244116"
---
1. Visual Studio での Web 配置にアプリケーションを配置する場合は、サーバーで Web Deploy の最新バージョンをインストールします。

    Web Deploy をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)します。 (IIS から Web Platform Installer のリンクを検索する選択**IIS**でサーバー マネージャーの左側のウィンドウ。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**)。

    Web Platform Installer で [アプリケーション] タブで、Web Deploy を紹介します。インストーラーを入手することも、 [Microsoft ダウンロード センター](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)します。 

2. Web Deploy が実行されて正しく開いて**コントロール パネル > システムとセキュリティ > 管理ツール > サービス**ことを確認し、 **Web Deployment Agent サービス**が実行されている (、サービス名が以前のバージョンでは異なる) です。

    エージェント サービスが実行されていない場合は、それを起動します。 それが存在しない場合を参照してください。**コントロール パネル > プログラム > プログラムのアンインストール**、検索**Microsoft Web Deploy <version>** します。 **変更**インストールを選択することを確認して**はローカル ハード ドライブにインストールされます**Web 配置のコンポーネント。 変更のインストール手順を完了します。