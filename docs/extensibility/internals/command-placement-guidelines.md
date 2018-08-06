---
title: コマンド配置のガイドライン |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bac09a361c885d866bf6a78e6fe7b49c246265ba
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511187"
---
# <a name="command-placement-guidelines"></a>コマンド配置のガイドライン
Visual Studio 統合開発環境 (IDE) でのコマンドを配置するためのベスト プラクティスは、コマンド セットのサイズによって異なります。 コマンドが定義されているし、情報に従って配置 *.vsct*ファイル。  
  
## <a name="best-practices-for-all-command-sets"></a>すべてのコマンド セットのベスト プラクティス  
 コマンドのセットはすべて、次のガイドラインに従います。  
  
-   コマンドの構造体のグラフを事前に準備します。 コマンド、コンボ ボックス、コマンド グループ、および複数の場所で使用されるショートカット メニューを特定します。  
  
-   同じグループ内に表示されるコマンドに関連付ける必要があります。  
  
-   1 つのコマンドを含むグループを利用できます。  
  
-   パッケージは、多くのコマンドを既存の Visual Studio のメニューに追加しないでください。 代わりに、メニューまたはサブメニューを新しいコマンドをホストするを作成する必要があります。  
  
-   配置すると、コマンド、名前のコマンドは、既存のメニューで目的がはっきりとはしない既存のコマンドで混乱するようにします。  
  
## <a name="best-practices-for-small-command-sets"></a>小規模なコマンド セットのベスト プラクティス  
 いくつかのコマンドを含む VSPackage を開発している場合は、これらのガイドラインに従っても。  
  
-   可能であればを使用して、[親](../../extensibility/parent-element.md)適切なグループに配置するコマンド、コンボ ボックス、グループ、または子メニューの要素。  
  
-   VSPackage によって表示されるメニューには、これらのグループを割り当てます。  
  
-   子メニューまたはコマンドの親である必要があります、[グループ](../../extensibility/group-element.md)要素。 コマンドおよび子メニュー グループに割り当てるし、親メニューに、グループを割り当てます。  
  
-   他のグループにコマンドを配置するには追加することで、 [CommandPlacements](../../extensibility/commandplacements-element.md)コマンド、し、追加の定義の後に要素のセクション、`CommandPlacements`要素、 [CommandPlacement](../../extensibility/commandplacement-element.md)要素各追加グループ。  
  
## <a name="best-practices-for-large-command-sets"></a>大量のコマンド セットのベスト プラクティス  
 VSPackage が複数のコンテキストで表示される多くのコマンドである場合は、次のガイドラインを次も実行します。  
  
-   メニューのグループ、および自己の親のコマンドを作成します。 つまり、割り当てないでください、`Parent`項目の定義内の要素。  
  
-   使用`CommandPlacement`要素のエントリ、`CommandPlacements`要素セクションには、グループの親メニューやメニューのグループ、およびコマンドを配置します。  
  
-   `CommandPlacements`要素セクションでは、特定のメニューまたはグループを設定するエントリは互いに隣接する必要があります。 読みやすくなり、この、`Priority`ランキングを容易に判断します。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)