---
title: このプロジェクトの作成に使用されるブックには、デザイナーで読み込めない ActiveX コントロールが含まれています
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8c42a1d1a6745daca8d83d3f21916253e70fdae
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867443"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>このプロジェクトの作成に使用されるブックには、デザイナーで読み込めない ActiveX コントロールが含まれています
  このエラーは、Word 文書または Excel ワークシートにプログラムでコントロールを追加し、その文書またはブックを保存して、保存した文書またはブックに基づいて新たなドキュメント レベルのソリューションを作成すると表示されます。  
  
 コントロールのマネージド型を記述した情報は、文書またはブックと共に保存されません。 このような文書またはブックに基づいて新しいソリューションを作成すると、コントロールをホスト項目デザイナーに読み込むのに必要な情報が Visual Studio に提供されません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  文書またはブックを開きます。  
  
2.  実行時に追加されたコントロールを削除します。 文書またはブックおよびキーを押してで選択してこれを行う、**削除**キー。  
  
3.  文書またはブックに基づいたドキュメント レベルのソリューションを作成します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)  
