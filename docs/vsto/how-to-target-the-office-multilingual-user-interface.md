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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39ee8b6bdcb4ad647164ec555cfa37ee9cfe8f50
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
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
  
  