---
title: '方法: Office の multilingual user interface します。'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180780835f36768cef77207189a1346c1dccdca
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866517"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>方法: Office の multilingual user interface します。
  Multilingual User Interface (MUI) は、ユーザー インターフェイス (UI) の言語を変更する機能をエンドユーザーに提供する Microsoft Office の機能です。 たとえば、英語の UI で作業している、エンドユーザーは、スペイン語に UI の言語を変更できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Office の多くの言語を使用するユーザー、アプリケーションを使用する場合は、自動的に (ユーザーにインストールされている適切なリソースがある場合)、ユーザーのコンピューターに Office で使用されている言語に一致するように、UI 文字列の言語を変更するコードを追加できます。  
  
## <a name="to-check-the-current-office-ui-setting"></a>現在の Office UI の設定を確認するには  
  
1.  使用して、<xref:System.Threading.Thread.CurrentUICulture%2A>現在のスレッドのプロパティ。 現在、ユーザーのコンピューターで実行されている Office のバージョンによって使用される言語に一致するように、UI 文字列の言語を設定します。  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プライマリ相互運用機能アセンブリを利用して Office アプリケーションします。](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)  
