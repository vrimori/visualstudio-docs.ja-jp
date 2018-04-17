---
title: コマンドの配置ガイドライン |Microsoft ドキュメント
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
ms.openlocfilehash: c406a5a34ea2556d367c8f7af8a9fda70fcc2676
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="command-placement-guidelines"></a>コマンドの配置ガイドライン
Visual Studio 統合開発環境 (IDE) でのコマンドの配置のベスト プラクティスは、コマンド セットのサイズによって異なります。 コマンドが定義されているし、.vsct ファイル内の情報に従って配置します。  
  
## <a name="best-practices-for-all-command-sets"></a>すべてのコマンド セットのベスト プラクティス  
 コマンドのセットはすべて、次のガイドラインに従ってください。  
  
-   コマンドの構造のグラフを事前に準備します。 コマンド、コンボ ボックス、コマンド グループ、および複数の場所で使用されるショートカット メニューを識別します。  
  
-   同じグループ内に表示されるコマンドを関連付ける必要があります。  
  
-   1 つのコマンドを含むグループは可能です。  
  
-   パッケージは、多くのコマンドを既存の Visual Studio のメニューに追加しないでください。 代わりに、メニューまたはサブメニューを新しいコマンドをホストを作成する必要があります。  
  
-   場合の目的が明確では、これと混同しない既存のコマンドされるように、名前のコマンドは、既存のメニューにコマンドを配置します。  
  
## <a name="best-practices-for-small-command-sets"></a>小さなコマンド セットのベスト プラクティス  
 いくつかのコマンドを含む VSPackage を開発している場合は、これらのガイドラインに従っても。  
  
-   可能であれば、使用、[親要素](../../extensibility/parent-element.md)の適切なグループに配置するコマンド、コンボ ボックス、グループ、または子メニュー。  
  
-   これらのグループを VSPackage によって表示されるメニューに割り当てます。  
  
-   子メニューやコマンドの親である必要があります、[グループ要素](../../extensibility/group-element.md)です。 コマンドおよび子メニュー グループを指定し、親メニューに、グループを割り当てます。  
  
-   追加することによって他のグループにコマンドを配置することができます、 [CommandPlacements 要素](../../extensibility/commandplacements-element.md)セクションのコマンドの定義の後にし、追加する、 `CommandPlacements Element` 、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)ごとその他のグループです。  
  
## <a name="best-practices-for-large-command-sets"></a>大量のコマンド セットのベスト プラクティス  
 VSPackage が複数のコンテキストで表示される多くのコマンドである場合は、次のガイドラインを次も実行します。  
  
-   メニューのグループ、および自己の親のコマンドを確認します。 つまり、割り当てないでください、`Parent Element`アイテムの定義にします。  
  
-   使用して`CommandPlacement Element`内のエントリ、`CommandPlacements Element`親メニューおよびグループに、メニューのグループ、およびコマンドを格納するセクション。  
  
-   `CommandPlacements`セクションで、指定されたメニューを設定するエントリまたはグループは互いに隣接する必要があります。 読みやすくなり、この、`Priority`ランク付けを容易に判断します。  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)