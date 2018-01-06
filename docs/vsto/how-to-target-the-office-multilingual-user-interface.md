---
title: "方法: Office Multilingual User Interface をターゲット |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3de0e73a4a5a5cf10cd0f378a2d00d3c4da1b2d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>方法 : Office Multilingual User Interface を使用する
  Multilingual User Interface (MUI) は、エンドユーザーのユーザー インターフェイス (UI) の言語を変更する機能を提供する Microsoft Office 機能です。 たとえば、英語の UI で作業している、エンドユーザーは、スペイン語に、UI の言語を変更できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Office の複数の言語を使用するユーザー、アプリケーションを使用する場合は、自動的に UI (ユーザーにインストールされている正しいリソースがある場合)、ユーザーのコンピューターで Office で使用されている言語と一致する文字列の言語を変更するコードを追加できます。  
  
### <a name="to-check-the-current-office-ui-setting"></a>Office UI の現在の設定を確認するには  
  
1.  使用して、<xref:System.Threading.Thread.CurrentUICulture%2A>現在のスレッドのプロパティです。 ユーザーのコンピューターで現在実行されている Office のバージョンで使用されている言語に合わせての UI 文字列の言語を設定します。  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>参照  
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)  
  
  