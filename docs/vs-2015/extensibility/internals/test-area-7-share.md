---
title: 'テスト領域 7: 共有 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31ef127e53a43cf018da5b78ed79a6b2145815da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548088"
---
# <a name="test-area-7-share"></a>テスト領域 7: 共有
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[テスト領域 7: 共有](https://docs.microsoft.com/visualstudio/extensibility/internals/test-area-7-share)します。  
  
このテストの領域を使用して場所の間で共有アイテムをカバーする、**共有**コマンド。  
  
 Hhare 操作では、ファイルとフォルダーの項目をソース コントロールのファイル階層内の 2 つまたは複数の場所の間での明らかな重複です。 重複はサーバーで、実際に発生しませんが、ユーザーは 2 つ以上の指定された場所に同じファイルを参照してください。 共有項目のいずれかに変更されるたびに、これらの変更が他のすべての共有場所に表示されます。  
  
 ソース管理下にある少なくとも 1 つのファイルとフォルダーを選択する場合、共有フォルダーには機能します。 [共有] コマンドは、次の条件下で無効になります。  
  
-   選択したフォルダーが空のフォルダーの場合は。  
  
-   実際のフォルダーがありますが、ソース管理ファイルを含んでいません。  
  
-   場合は、仮想フォルダーがあるソース管理下にあるファイルがあるかどうかどうか。  
  
-   リモート サイトの Web プロジェクトがある場合  
  
## <a name="command-menu-access"></a>コマンド メニューへのアクセス  
 次[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境のメニューのパスは、テスト_ケースで使用されます。  
  
 共有:**ファイル**->**ソース管理**->**共有**します。  
  
## <a name="expected-behavior"></a>想定される動作  
  
-   共有ファイルは、共有の場所が表示されます。  
  
-   ファイルが共有されるソース コントロールのバージョン ストア履歴表示を表示します。  
  
-   ファイルの両方の場所を編集、共有ファイルを編集します。  
  
## <a name="test-cases"></a>テスト ケース  
 共有テスト領域の特定のテスト_ケースを次に示します。  
  
|アクション|テスト ステップ|予想される結果を確認します|  
|------------|----------------|--------------------------------|  
|読み込まれている別のプロジェクトをソース管理下にある読み込まれている 1 つのプロジェクトからのファイルを共有します。|1.新しいプロジェクトを作成します。<br />2.2 つ目のプロジェクトをソリューションに追加します。<br />3.最初のプロジェクトではない名前の 2 つ目のプロジェクトでファイルを作成します。<br />4.ソース管理にソリューションを追加します。<br />5.最初のプロジェクトを選択します。<br />6.開いている**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />7.最初のプロジェクトに 2 つ目のプロジェクトからファイルを共有します。<br />8.受け入れる**チェック アウト**求められた場合。|一般的な想定される動作です。|  
|1 つのプロジェクトから別のファイルを共有します。|1.新しいプロジェクトを作成します。<br />2.ソース管理に追加します。<br />3.ソリューションを閉じます。<br />4.プロジェクトを作成する 2 つ目 (新しいソリューションです。)<br />5.ソース管理にソリューションを追加します。<br />6.プロジェクトを選択します。<br />7.開く、**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />8.開いているプロジェクトに追加した以前のプロジェクトからファイルを共有します。<br />9.受け入れる**チェック アウト**求められた場合。|一般的な想定される動作です。|  
|現在読み込まれているプロジェクトにソース管理からプロジェクトの一部ではないファイルを共有します。|1.新しいプロジェクトを作成します。<br />2.ソース管理にソリューションを追加します。<br />3.プロジェクトまたはソリューションの一部でないソース管理にファイルを追加します。<br />4.プロジェクトを選択し、開く、**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />5.内でファイルを選択して、**共有**ダイアログ ボックスを現在のプロジェクトまたはソリューション内に存在して共有することはできません。<br />6.受け入れる**チェック アウト**求められた場合。|ソース管理ストアを Get を実行してため、ファイルは、プロジェクトのローカルの場所にようになりました。|  
|別のフォルダーに、同じプロジェクト内のファイルを共有します。|1.選択**自動的にチェック アウト**で**ツール** -> **オプション** -> **ソース管理**します。<br />2.新しいプロジェクトを作成し、ソース管理に追加します。<br />3.フォルダーをプロジェクトに追加します。<br />4.フォルダーにファイルを追加し、フォルダーで確認してください。<br />5.フォルダーを選択します。<br />6.開いている**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />7.選択したフォルダーにファイルを共有します。|一般的な想定される動作です。<br /><br /> フォルダーは、共有を使用することで、ファイルでチェックインする必要があります。|  
|読み込まれているプロジェクトにフォルダーを共有する-再帰|1.新しいプロジェクトを作成します。<br />2.ソース管理にソリューションを追加します。<br />3.プロジェクトを選択します。<br />4.開く、**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />5.フォルダーを選択します。<br />6.プロジェクトに再帰的にフォルダーを共有します。|一般的な想定される動作です。|  
|1 つのプロジェクトからの複数のファイルを別の共有します。|1.いくつかのファイルには、新しいプロジェクトを作成します。<br />2.ソース管理にソリューションを追加します。<br />3.ソリューションを閉じます。<br />4.新しいソリューションに新しいプロジェクトを作成します。<br />5.ソース管理にソリューションを追加します。<br />6.プロジェクトを選択します。<br />7.開く、**共有** ダイアログ ボックス (**ファイル** -> **ソース管理** -> **共有**)。<br />8.現在開いているプロジェクトを以前に作成したプロジェクトから複数のファイルを共有します。|一般的な想定される動作です。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン向けのテスト ガイド](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
