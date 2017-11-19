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
ms.openlocfilehash: 2d82fc0eb60b2680be9ed2bdb7de13313593da0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
1. Visual Studio での Web 配置でアプリケーションを配置する場合は、サーバーで Web Deploy の最新バージョンをインストールします。

    Web Deploy をインストールするには、使用、 [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)から直接、インストーラーを入手または、 [Microsoft ダウンロード センター](https://www.microsoft.com/search/result.aspx?q=webdeploy&form=dlc)です。 [アプリケーション] タブで Web Deploy 検索します。 

2. Web Deploy が実行される確認正しく開くことによって**コントロール パネル > システムとセキュリティ > 管理ツール > サービス**ことを確認および**Web Deployment Agent サービス**が実行されている (サービス名は旧バージョンでは異なる) です。

    エージェント サービスが実行されていない場合は、それを開始します。 これが存在しない場合を参照してください。**コントロール パネル > プログラム > プログラムのアンインストール**、検索**Microsoft Web Deploy <version>**です。 選択**変更**インストールを選択することを確認し、**はローカル ハード ドライブにインストールする**Web 配置のコンポーネントです。 変更のインストール手順を完了します。