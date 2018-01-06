---
title: "方法: 引数デザイナーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aa1cdd0dd563a5f87d4e32f779985afd63319032
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-argument-designer"></a>引数デザイナーを使用する方法
[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の以前のバージョンと比べ、引数デザイナーを使用した場合は、アクティビティとの間のデータの受け渡しを簡単に実行できます。 デザイナーにアクセスする をクリックして、**引数**デザイン キャンバスの左下隅にあるボタンをクリックします。 デザイナーには以外の各列見出しで並べ替えることができます、表形式で表示されている引数の一覧が含まれています、**既定値**列です。 各引数には、名前、方向 (入力、出力、入力/出力、またはプロパティ)、型、および既定の式の値 (存在する場合) が含まれます。 名前および既定の式の値は編集可能なテキスト フィールドで、型および方向はドロップダウンです。 [!含める[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)です。  
  
### <a name="to-create-a-new-argument"></a>新しい引数を作成するには  
  
1.  [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] でワークフロー ソリューションまたはアクティビティ ソリューションを開きます。  
  
2.  クリックして、引数デザイナーを開き、**引数**デザイン キャンバスの左下隅にあるボタンをクリックします。 引数デザイナーが表示されます。  
  
3.  ラベルの付いた空の行をクリックして**引数の作成**です。 次の既定値を使用して、新しい引数を持つ新しい行追加されます: の argumentx、**名前**x は一意の引数名を作成して自動的にインクリメントされる 1 の初期値を持つ整数**で**の**方向**、および**文字列**の**引数の型**です。 値は追加されません**既定値**です。 これらの値は、ワークフローのデザイン プロセス中にいつでも変更できます。  
  
    > [!NOTE]
    >  削除する引数、引数をクリックして選択し、キーを押します、**削除**キー。  
  
## <a name="see-also"></a>参照  
 [ワークフロー デザイナーの使用](../workflow-designer/using-the-workflow-designer.md)   
 [変数と引数](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)