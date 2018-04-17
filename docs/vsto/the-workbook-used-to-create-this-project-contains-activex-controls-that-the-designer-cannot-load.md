---
title: このプロジェクトの作成に使用されるブックには、デザイナーで読み込めない ActiveX コントロールが含まれています |。Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d31674f54ce454db50a63572c24f92031e7d886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>このプロジェクトの作成に使用されるブックには、デザイナーで読み込めない ActiveX コントロールが含まれています
  このエラーは、Word 文書または Excel ワークシートにプログラムでコントロールを追加し、その文書またはブックを保存して、保存した文書またはブックに基づいて新たなドキュメント レベルのソリューションを作成すると表示されます。  
  
 コントロールのマネージ型を記述した情報は、文書またはブックと共に保存されません。 このような文書またはブックに基づいて新しいソリューションを作成すると、コントロールをホスト項目デザイナーに読み込むのに必要な情報が Visual Studio に提供されません。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  文書またはブックを開きます。  
  
2.  実行時に追加されたコントロールを削除します。 この操作は、文書またはブックで対象のコントロールを選択し、Delete キーを押すことで実行できます。  
  
3.  文書またはブックに基づいたドキュメント レベルのソリューションを作成します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  