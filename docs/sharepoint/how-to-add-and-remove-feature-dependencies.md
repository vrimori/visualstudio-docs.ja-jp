---
title: '方法: 追加および機能の依存関係を削除する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65963c43c5a4facd8a3ca7c0f8ab1ed1988342f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767791"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>方法: 追加および機能の依存関係を削除します。
  SharePoint の機能は、機能やデータの他の機能によって異なります。 このような場合は、これら他の機能を機能の依存関係としてマークできます。 これにより、SharePoint サーバーにより、機能をアクティブ化する前に、依存する機能がアクティブ化されます。  
  
## <a name="adding-dependencies"></a>依存関係の追加  
 依存関係として、ソリューション内の他の機能を追加できます。 このようにすることができます必要な機能がインストールされ、機能をインストールする前にアクティブ化されていることを確認します。  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>ソリューション内のフィーチャーの依存関係を追加するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係** ノードを選択し、**追加**ボタンをクリックします。  
  
2.  **機能のアクティブ化依存関係の追加** ダイアログ ボックスで、選択、**ソリューションの機能の依存関係を追加** ボタンをオプションで、依存関係として追加する機能のタイトルを選択し、選択、**追加**ボタンをクリックします。  
  
     選択中に複数のタイトルを選択して 1 つ以上の機能を追加することができます、 **Ctrl**キー。  
  
## <a name="adding-custom-dependencies"></a>カスタム依存関係の追加  
 依存関係として、SharePoint サーバーに既に配置されている機能を追加できます。 これにより、SharePoint のライセンス認証プロセスは、機能をインストールする前に、すべての依存する機能をアクティブ化されるかどうかを確認するを確認します。  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>機能 ID で依存関係を追加するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係** ノードを選択し、**追加**ボタンをクリックします。  
  
2.  **機能のアクティブ化依存関係の追加** ダイアログ ボックスで、選択、**カスタム依存関係を追加**オプション ボタンをクリックします。  
  
3.  **機能 ID**テキスト ボックスに、アクティブ化依存関係としてマークし、選択する機能の GUID を入力、**追加**ボタンをクリックします。  
  
## <a name="editing-custom-dependencies"></a>カスタム依存関係の編集  
 前に追加したカスタムの依存関係を編集することができます。 ただしはソリューションできますのみが削除される、依存する機能は編集できません。  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>ソリューション内のフィーチャーの依存関係を変更するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係**ノード。  
  
2.  クリックして、編集する機能の名前を選択して、**編集**ボタンをクリックします。  
  
3.  **カスタム フィーチャー アクティブ化依存関係を編集**] ダイアログ ボックスは、タイトル フィーチャー ID、または説明を変更し、[、**送信**ボタンをクリックします。  
  
## <a name="removing-dependencies"></a>依存関係を削除します。  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>ソリューションのフィーチャーの依存関係を削除するには
  
1.  フィーチャー デザイナーで、展開、**機能のアクティブ化依存関係** ノードを削除して、順に選択する機能の名前を選択、**削除**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目
 [SharePoint フィーチャーの作成](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズ](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: SharePoint フィーチャーの項目を追加および削除する](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
