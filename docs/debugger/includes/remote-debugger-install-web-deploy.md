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
ms.openlocfilehash: 81b58a2162d7240e32e1fb2d45e462ec551155e7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
1. Visual Studio での Web 配置でアプリケーションを配置する場合は、サーバーで Web Deploy の最新バージョンをインストールします。

    Web Deploy をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)です。 [アプリケーション] タブで Web Deploy 検索します。直接インストーラーを入手することも、 [Microsoft ダウンロード センター](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)です。 

2. Web Deploy が実行される確認正しく開くことによって**コントロール パネル > システムとセキュリティ > 管理ツール > サービス**ことを確認および**Web Deployment Agent サービス**が実行されている (サービス名は旧バージョンでは異なる) です。

    エージェント サービスが実行されていない場合は、それを開始します。 これが存在しない場合を参照してください。**コントロール パネル > プログラム > プログラムのアンインストール**、検索**Microsoft Web Deploy <version>**です。 選択**変更**インストールを選択することを確認し、**はローカル ハード ドライブにインストールする**Web 配置のコンポーネントです。 変更のインストール手順を完了します。