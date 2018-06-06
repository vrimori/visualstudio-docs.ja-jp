---
title: サーバー エクスプ ローラーを使用した SharePoint 接続を参照 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d19dc2cb621cc99b94524806d63eebba137668a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765857"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>サーバー エクスプ ローラーを使用して、SharePoint 接続を参照します。
  ローカルの SharePoint 接続を表示できるようになりました**サーバー エクスプ ローラー**です。 この手法を使用すると、システムに SharePoint サイトのコンポーネント間を移動できます。 という名前のノードに表示されるリストの定義およびコンテンツの種類など、SharePoint サイトのコンポーネント**SharePoint 接続**のツリー ビューで**サーバー エクスプ ローラー**です。 表示する**サーバー エクスプ ローラー**、メニュー バーで、次のように選択します。**ビュー** > **サーバー エクスプ ローラー**です。 SharePoint サイトのコンポーネントを表示するだけでなく項目を削除する、そのプロパティを表示したり、ショートカット メニューのコマンドを使用して、ツリー ビューを更新できます。  
  
> [!IMPORTANT]  
>  SharePoint サイトを参照するには、SharePoint サイト コレクションの管理者であるし、ローカル コンピューターの管理者として Visual Studio を実行する必要があります。 サイトは、それ以外の場合、**サーバー エクスプ ローラー**、そのノードを展開することはできませんが、します。 サイト コレクションの管理者であるかどうかを確認するには、開いている web ブラウザーでサイトを開く、**サイトの操作** メニューの 選択**サイトのアクセス許可**、、**アクセス許可: チームサイト**ページで、選択、**サイト コレクション管理者**コマンドを**管理**リボンのグループ化します。 自分の名前は、サイト コレクションの管理者がいる場合、テキスト ボックスに表示されます。 場合、**サイト コレクション管理者**コマンドがリボン上の管理グループに表示されない、サイト コレクションの管理者でないし、サイト管理者から適切なアクセス許可を取得する必要があります。  
  
## <a name="server-explorer-nodes"></a>サーバー エクスプ ローラー ノード
 SharePoint サイトのすべてのコンポーネントが内のノードによって表される、**サーバー エクスプ ローラー**ツリー ビューで**SharePoint 接続**です。 たとえば、既定の SharePoint サイトに含める詳細についてに表示されるディスカッションの型を表すと呼ばれるコンテンツの種類、**ディスカッション**SharePoint サイトのページです。 ディスカッション コンテンツの種類には、いくつかのフィールドが含まれています。 これらのフィールドを表示する**サーバー エクスプ ローラー**、展開、**コンテンツ タイプ**ノード、し、**ディスカッション**ノード。 本文、ディスカッション件名や Title などのいくつかのフィールド ノードがします。  
  
## <a name="node-shortcut-menu-commands"></a>ノードのショートカット メニューのコマンド
 各ノードにノードを右クリックしてまたは選択し を選択してアクセスされるショートカット メニュー、 **Shift**+**F10**キー。 ノードのコマンドは、次に示します。  
  
|コマンド名|説明|  
|------------------|-----------------|  
|最新の情報に更新|最後に、ノードが表示されてから発生した変更を反映するように、ツリー ビューを更新します。|  
|削除|ツリー ビューから選択したノードを削除します。 **注:** 下に表示する SharePoint 接続でのみこのコマンドが有効になっている、 **SharePoint 接続**ノード。|  
|プロパティ|選択されたノードの使用可能なプロパティを表示、**プロパティ**ウィンドウです。 プロパティはすべて読み取り専用、およびすべてのノードが関連付けられているプロパティ。|  
|接続の追加|SharePoint サイトを参照するを指定できます。 使用できる、 **SharePoint 接続**ノードとサブ サイト ノード。|  
|ブラウザーで表示|Web ブラウザーで選択した一覧を表示します。 このコマンドは、いくつかのリストの下で使用できる、**一覧**ノードに含まれている**リストとライブラリ**です。|  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: SharePoint 接続を追加または削除する](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|新しい SharePoint サイトを追加するために必要な手順について説明します、 **SharePoint 接続**内のノード**サーバー エクスプ ローラー**です。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
  
 