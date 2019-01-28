---
title: '方法: 追加および削除機能の依存関係 |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baedf731a61a13bd6592298e8505dc4a445819e1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871898"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>方法: 追加および削除機能の依存関係
  SharePoint の機能は、機能またはデータのための他の機能によって異なります。 このような場合、機能の依存関係としてこれらの他の機能をマークできます。 これにより、SharePoint サーバーにより、機能をアクティブ化する前に、依存する機能がアクティブ化されます。  
  
## <a name="add-dependencies"></a>依存関係を追加する  
 依存関係として、ソリューション内の他の機能を追加できます。 これにより、行うことができます必要な機能がインストールされ、機能をインストールする前にアクティブ化されることを確認します。  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>ソリューション内のフィーチャーの依存関係を追加するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係**ノードを選択し、**追加**ボタンをクリックします。  
  
2.  **機能のアクティブ化依存関係の追加** ダイアログ ボックスで、選択、**ソリューションの機能の依存関係を追加**オプション ボタンを依存関係として追加する機能のタイトルを選択し、選択、**追加**ボタンをクリックします。  
  
     選択しながら複数のタイトルを選択して 1 つ以上の機能を追加することができます、 **Ctrl**キー。  
  
## <a name="addi-custom-dependencies"></a>今後のカスタム依存関係  
 依存関係として、SharePoint サーバーに既に配置されている機能を追加できます。 これにより、機能をインストールする前に、すべての依存機能がアクティブ化されるかどうかを確認する、SharePoint のライセンス認証プロセスを確認します。  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>機能 ID で依存関係を追加するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係**ノードを選択し、**追加**ボタンをクリックします。  
  
2.  **機能のアクティブ化依存関係の追加** ダイアログ ボックスで、選択、**カスタム依存関係を追加**オプション ボタンをクリックします。  
  
3.  **機能 ID**テキスト ボックスに、クリックして、アクティブ化依存関係としてマークする機能の GUID を入力、**追加**ボタンをクリックします。  
  
## <a name="edit-custom-dependencies"></a>カスタム依存関係を編集します。  
 前に追加したカスタムの依存関係を編集することができます。 ただし、ソリューションことができますのみである削除された、依存する機能は編集できません。  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>ソリューション内のフィーチャーの依存関係を変更するには
  
1.  フィーチャー デザイナーを開き、展開、**機能のアクティブ化依存関係**ノード。  
  
2.  編集、および選択する機能の名前を選択、**編集**ボタンをクリックします。  
  
3.  **カスタム フィーチャー アクティブ化依存関係を編集**] ダイアログ ボックスでは、タイトル、機能の ID または説明を変更し、[、**送信**ボタンをクリックします。  
  
## <a name="remove-dependencies"></a>依存関係を削除します。  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>ソリューションの機能への依存関係を削除するには
  
1.  フィーチャー デザイナーで、展開、**機能のアクティブ化依存関係**ノード、して選択し、削除、希望する機能の名前を選択、**削除**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目
 [SharePoint の機能を作成します。](../sharepoint/creating-sharepoint-features.md)   
 [方法: SharePoint フィーチャーをカスタマイズします。](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [方法: 項目を SharePoint の機能を追加および削除](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
