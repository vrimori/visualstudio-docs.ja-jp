---
title: '方法: 引数デザイナーを使用して |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: eaff53dc04c0ad2367147ae91c7de756e5ca4366
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537637"
---
# <a name="how-to-use-the-argument-designer"></a>引数デザイナーを使用する方法
[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の以前のバージョンと比べ、引数デザイナーを使用した場合は、アクティビティとの間のデータの受け渡しを簡単に実行できます。 デザイナーにアクセスする をクリックして、**引数**デザイン キャンバスの左下隅のボタンをクリックします。 デザイナーには、表形式で表示され、以外の各列見出しで並べ替えることができますを引数のリストが含まれています、**既定値**列。 各引数には、名前、方向 (入力、出力、入力/出力、またはプロパティ)、型、および既定の式の値 (存在する場合) が含まれます。 名前および既定の式の値は編集可能なテキスト フィールドで、型および方向はドロップダウンです。 [!INCLUDE[crabout](../includes/crabout-md.md)] 引数を参照してください[変数と引数](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)します。  
  
### <a name="to-create-a-new-argument"></a>新しい引数を作成するには  
  
1.  [!INCLUDE[vs2010](../includes/vs2010-md.md)] でワークフロー ソリューションまたはアクティビティ ソリューションを開きます。  
  
2.  クリックして、引数デザイナーを開き、**引数**デザイン キャンバスの左下隅のボタンをクリックします。 引数デザイナーが表示されます。  
  
3.  というラベルの付いた空の行をクリックします。**引数の作成**です。 これは、新しい行が次の既定値を使用して新しい引数を指定して追加されます: の argumentx、**名前**x は一意の引数の名前を作成する自動的にインクリメントされる 1 の初期値を持つ整数**で**の**方向**、および**文字列**の**引数の型**します。 値は追加されません**既定値**します。 これらの値は、ワークフローのデザイン プロセス中にいつでも変更できます。  
  
    > [!NOTE]
    >  引数を削除するをクリックして、引数を選択し、キーを押します、**削除**キー。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー デザイナーの使用](../workflow-designer/using-the-workflow-designer.md)   
 [変数と引数](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)