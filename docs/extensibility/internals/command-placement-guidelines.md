---
title: "コマンドの配置ガイドライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca84800a199e9db420379697051fece598eb9295
ms.lasthandoff: 02/22/2017

---
# <a name="command-placement-guidelines"></a>コマンドの配置ガイドライン
Visual Studio 統合開発環境 (IDE) でのコマンドを配置するためのベスト プラクティスは、コマンド セットのサイズによって異なります。 コマンドでは、定義され、.vsct ファイルの情報に従って配置することができます。  
  
## <a name="best-practices-for-all-command-sets"></a>すべてのコマンド セットのベスト プラクティス  
 コマンドの各セットでは、次のガイドラインに従ってください。  
  
-   コマンドの構造のグラフを事前に準備します。 コマンド、コンボ ボックス、コマンドのグループ、および複数の場所で使用されるショートカット メニューを識別します。  
  
-   同じグループ内に表示されるコマンドが関連付けられている必要があります。  
  
-   1 つのコマンドを含むグループは、許容されます。  
  
-   パッケージは、多くのコマンドを既存の Visual Studio のメニューに追加しないでください。 代わりに、メニューやサブメニューを新しいコマンドをホストするを作成する必要があります。  
  
-   その目的は、クリアし、既存のコマンドとは区別されますがされるように、名前のコマンドは、既存のメニューにコマンドを配置します。  
  
## <a name="best-practices-for-small-command-sets"></a>小規模のコマンド セットのベスト プラクティス  
 いくつかのコマンドを含む VSPackage を開発する場合は、次のガイドラインを次も実行します。  
  
-   可能であれば、使用、[親要素](../../extensibility/parent-element.md)の適切なグループに配置するコマンド、コンボ ボックス、グループ、または子メニュー。  
  
-   VSPackage で表示されるメニューには、これらのグループを割り当てます。  
  
-   子メニューまたはコマンドの親である必要があります、[グループ要素](../../extensibility/group-element.md)します。 コマンドと子メニュー グループを指定し、親メニューに、グループを割り当てます。  
  
-   他のグループにコマンドを配置するには追加することで、 [CommandPlacements 要素](../../extensibility/commandplacements-element.md)セクションのコマンドの定義の後にし、追加する、 `CommandPlacements Element` 、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)追加グループごとにします。  
  
## <a name="best-practices-for-large-command-sets"></a>大量のコマンド セットのベスト プラクティス  
 予定の場合、VSPackage は複数のコンテキストで表示されるコマンドの多く、これらのガイドラインに従ってくださいも。  
  
-   メニューのグループ、および自己の親のコマンドを確認します。 つまり、割り当てないでください、`Parent Element`アイテムの定義にします。  
  
-   使用`CommandPlacement Element`内のエントリ、`CommandPlacements Element`による親メニューとグループにメニューのグループ、およびコマンドを格納するセクションです。  
  
-   `CommandPlacements`セクションで、指定されたメニューを設定するエントリまたはグループは互いに隣接する必要があります。 読みやすくなり、この、`Priority`ランキングをより簡単に判断します。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
