---
title: サーバー エクスプ ローラーを使用した SharePoint 接続の参照 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 825bf975d877cd6b0844e86aabff605daa30a900
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875486"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>サーバー エクスプ ローラーを使用して SharePoint 接続を参照します。
  ローカルの SharePoint 接続を表示できるようになりました**サーバー エクスプ ローラー**します。 この手法を使用すると、システム上の SharePoint サイトのコンポーネントを移動できます。 という名前のノードに表示されるリストの定義およびコンテンツの種類など、SharePoint サイトのコンポーネント**SharePoint 接続**のツリー ビューで**サーバー エクスプ ローラー**します。 表示する**サーバー エクスプ ローラー**、メニュー バーで、**ビュー** > **サーバー エクスプ ローラー**します。 SharePoint サイトのコンポーネントを表示するだけでなく項目を削除のプロパティを表示したり、ショートカット メニューのコマンドを使用して、ツリー ビューを更新できます。  
  
> [!IMPORTANT]  
>  SharePoint サイトを参照するには、SharePoint サイト コレクションの管理者であるし、ローカル コンピューターの管理者として Visual Studio を実行する必要があります。 サイトは、それ以外の場合、**サーバー エクスプ ローラー**が、そのノードを展開することはできません。 サイト コレクションの管理者であるかどうかを確認するには、開いている web ブラウザーでサイトを開く、**サイトの操作**] メニューの [選択**サイトのアクセス許可**、し、**アクセス許可。チーム サイト**ページで、選択、**サイト コレクション管理者**コマンドから、**管理**リボンのグループ化します。 自分の名前は、サイト コレクションの管理者である場合、テキスト ボックスに表示されます。 場合、**サイト コレクション管理者**コマンドがリボン上の管理グループに表示されない、サイト コレクションの管理者でないし、サイト管理者から適切なアクセス許可を取得する必要があります。  
  
## <a name="server-explorer-nodes"></a>サーバー エクスプ ローラー ノード
 SharePoint サイトのすべてのコンポーネントがノードによって表される、**サーバー エクスプ ローラー**ツリー ビューで**SharePoint 接続**します。 たとえば、既定の SharePoint サイトに含める詳細については、表示するディスカッション型を表すと呼ばれるコンテンツの種類、**ディスカッション**SharePoint サイトのページ。 ディスカッションのコンテンツ タイプには、いくつかのフィールドが含まれています。 これらのフィールドを表示する**サーバー エクスプ ローラー**、展開、 **ContentTypes**ノードをクリックし、**ディスカッション**ノード。 本文、件名のディスカッション、およびタイトルなど、いくつかのフィールド ノードが。  
  
## <a name="node-shortcut-menu-commands"></a>ノードのショートカット メニューのコマンド
 各ノードでノードを右クリックしてまたは選択するか、クリックしてアクセスできるショートカット メニューには、 **Shift**+**F10**キー。 Node のコマンドは、次に示します。  
  
|コマンド名|説明|  
|------------------|-----------------|  
|最新の情報に更新|最後に、ノードが表示されてから発生したすべての変更を反映するように、ツリー ビューを更新します。|  
|削除|ツリー ビューから選択したノードを削除します。 **注:** このコマンドが下に表示する SharePoint 接続でのみ有効になっている、 **SharePoint 接続**ノード。|  
|プロパティ|選択されたノードの使用可能なプロパティを表示、**プロパティ**ウィンドウ。 プロパティはすべて読み取り専用、およびすべてのノードが関連付けられているプロパティ。|  
|接続の追加|SharePoint サイトを参照するを指定することができます。 使用できる、 **SharePoint 接続**ノードとサブ サイト ノード。|  
|ブラウザーで表示|Web ブラウザーでは、選択した一覧を表示します。 このコマンドは、いくつかの下に一覧で使用できる、**一覧**ノードに含まれている**リストとライブラリ**します。|  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: 追加または SharePoint 接続の削除](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|新しい SharePoint サイトを追加するために必要な手順について説明します、 **SharePoint 接続**ノード**サーバー エクスプ ローラー**します。|  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)  
