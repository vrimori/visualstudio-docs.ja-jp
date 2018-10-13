---
title: モデル エクスプ ローラーのカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 77999eea0a76088368ff5e7ee66f9088dc45efa5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175943"
---
# <a name="customizing-the-model-explorer"></a>モデル エクスプローラーのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

変更、エクスプ ローラーの動作と外観をドメイン固有言語デザイナーのとおり。  
  
-   ウィンドウのタイトルを変更します。  
  
-   タブ アイコンを変更します。  
  
-   ノードのアイコンを変更します。  
  
-   ノードを非表示にします。  
  
## <a name="changing-the-window-title"></a>ウィンドウのタイトルを変更します。  
 生成された、エクスプ ローラーのウィンドウのタイトルを変更するには、選択**エクスプ ローラーの動作**で、 **DSL エクスプ ローラー**、し、**プロパティ**ウィンドウで、設定、 **タイトル**プロパティを使用タイトル。  
  
## <a name="changing-the-tab-icon"></a>タブ アイコンを変更します。  
 エクスプ ローラーのタブのアイコンを変更するには、.bmp ファイルの 16 x 16 ピクセルのアイコンを使用します。 \DslPackage\Resources\ フォルダーにアイコン ファイルを配置し、ファイル名を変更して、 **ModelExplorerToolWindowBitmaps.bmp**します。 たとえば、変更する可能性があります、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] setup.ico アイコン ファイル .bmp 形式にして変更**DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**します。 生成されたデザイナー アイコンが表示されますこのエクスプ ローラーのタブと同時にドッキングされている**ソリューション エクスプ ローラー**します。  
  
## <a name="setting-custom-icons-on-explorer-nodes"></a>エクスプ ローラーのノードにカスタム アイコンを設定します。  
 エクスプ ローラー ノードの設定を使用して、エクスプ ローラーでノードをカスタマイズできます。 次の手順では、ノードにアイコンを追加する方法を示します。  
  
#### <a name="to-add-an-icon-to-an-explorer-node"></a>エクスプ ローラーのノードにアイコンを追加するには  
  
1.  作成、 [!INCLUDE[dsl](../includes/dsl-md.md)] Task Flow ソリューション テンプレートを使用してソリューション。  
  
2.  16 x 16 ピクセルのアイコンを含む .bmp ファイルを配置、 **dsl \resources**ソリューションのフォルダー。  
  
3.  **DSL エクスプ ローラー**、右クリックして**エクスプ ローラーの動作**順にクリックします**エクスプ ローラー ノードの新しい設定の追加**します。  
  
     **ExplorerNodeSettings**ノードが表示されます、**カスタム ノード設定**ノード。  
  
4.  選択**ExplorerNodeSettings**、し、**プロパティ**ウィンドウで、設定**クラス**に**アクター**します。  
  
5.  設定**アイコンを表示する**アイコン ファイルのパスにします。  
  
6.  すべてのテンプレートの変換およびビルドして、ソリューションを実行します。  
  
7.  生成されたデザイナーでは、図のサンプルを開きます。  
  
     エクスプ ローラーは、3 つを表示する必要があります**アクター**アイコンがあるノード。  
  
> [!NOTE]
>  生成された、エクスプ ローラーに表示される任意の要素のノードのアイコンを設定すると、エクスプ ローラーのすべてのノードにアイコンが表示されます。 アイコンが設定されていない場合、ノードの既定のアイコンが表示されます。  
  
## <a name="changing-the-name-displayed-on-an-explorer-node"></a>エクスプ ローラーのノードに表示される名前を変更します。  
 エクスプ ローラーでモデル要素の名前を表示する方法を変更することができます。 名前を表示する方法は、次の手順、**タスク**によって参照される、**コメント**コメント ノードにします。  
  
#### <a name="to-display-a-property"></a>プロパティを表示するには  
  
1.  前の手順で作成したソリューションを開きます。  
  
2.  確認、**コメント**プロパティの名前を持つロールの多重度を設定して 1 つのドメイン クラスのみを参照して**サブジェクト**0..1 にします。 プロパティ名になる**サブジェクト**、リレーションシップの名前になると**CommentReferencesSubject**します。  
  
3.  **DSL エクスプ ローラー**、右クリックして**エクスプ ローラーの動作**順にクリックします**エクスプ ローラー ノードの新しい設定の追加**します。  
  
     **ExplorerNodeSettings**ノードが表示されます、**カスタム ノード設定**ノード。  
  
4.  選択**ExplorerNodeSettings**、し、**プロパティ**ウィンドウで、設定**クラス**に**コメント**します。  
  
5.  右クリックし、**コメント**ノード、およびクリック**新しいプロパティのパスを追加**します。  
  
     新しいノードでは、という名前が表示されます**プロパティが表示される**します。  
  
6.  選択**プロパティを表示**、し、**プロパティ**ウィンドウの値フィールドをクリックします。**パスにプロパティ**。 選択**コメント**、し**CommentReferencesSubject**、し**FlowElement**します。 結果として得られるパスのようになります**CommentReferencesSubject.Subject/!サブジェクト**します。  
  
7.  値フィールドに**プロパティ**、**名前**します。  
  
8.  すべてのテンプレートの変換およびビルドして、ソリューションを実行します。  
  
9. 生成されたデザイナーでは、図のサンプルを開きます。  
  
10. 描画を**コメント コネクタ**コメント要素の間、 **Task1**図上の要素。  
  
     エクスプ ローラーのノードは、コメントに表示する必要があります**Task1**します。  
  
## <a name="hiding-nodes"></a>ノードを非表示  
 パスを追加することで、エクスプ ローラーでノードを非表示にできます、**隠しノード**のノード、 **DSL エクスプ ローラー**します。 次の手順は、非表示にする方法を示しています。**コメント**ノード。  
  
#### <a name="to-hide-an-explorer-node"></a>エクスプ ローラーのノードを非表示にするには  
  
1.  前の手順で作成したソリューションを開きます。  
  
2.  **DSL エクスプ ローラー**、右クリック**エクスプ ローラーの動作**順にクリックします**新しいドメインの追加パス**します。  
  
     A**ドメイン パス**ノードが表示されます**隠しノード**します。  
  
3.  選択**ドメイン パス**、し、**プロパティ**ウィンドウの値フィールドをクリックします。**パスの定義**します。 選択**フローグラフ**、し**FlowGraphHasComments**します。 結果として得られるパスのようになります**FlowGraphHasComments.Comments**  
  
4.  すべてのテンプレートの変換およびビルドして、ソリューションを実行します。  
  
5.  生成されたデザイナーでは、図のサンプルを開きます。  
  
     エクスプ ローラーのみを表示する必要があります、**アクター**ノードを表示しないと、**コメント**ノード。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



