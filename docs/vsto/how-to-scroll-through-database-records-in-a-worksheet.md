---
title: '方法: ワークシート内のデータベース レコードをスクロールします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1459ee941a8cb88d102e14ccfc7f128796c4c333
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897471"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>方法: ワークシート内のデータベース レコードをスクロールします。
  次の手順では、デザイナーを使用して、エンドユーザーがすべてのレコードをスクロールできるようにするコントロールでの Microsoft Office Excel ワークシートで、データベース テーブルから 1 つのフィールドを表示する方法を示します。  
  
 ドキュメント レベルのプロジェクトでのみ、デザイナーを使用することができます。 ただし、コントロールを追加し、実行時にプログラムでデータにバインドすることができますも。 詳細については、「[チュートリアル:VSTO アドイン プロジェクトでの単純データ バインディング](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>ワークシート内のデータベース レコードをスクロールするには  
  
1.  Visual Studio で Excel のアプリケーション プロジェクトを開きます。  
  
2.  開く、**データ ソース**ウィンドウと、データベースからデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。  
  
3.  を表示するデータを含むテーブルを展開し、特定の列を選択します。  
  
4.  コントロールのリストを開く**NamedRange**します。  
  
5.  ドラッグ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをデータが表示されるセルにします。  
  
6.  **Windows フォーム**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.BindingNavigator>ワークシートに制御し、使用するコントロールを設定します。 詳細については、次を参照してください。 [BindingNavigator コントロールの概要&#40;Windows フォーム&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)  
