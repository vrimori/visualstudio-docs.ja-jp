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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47a95db3797592f4c8d55ffa72e0e7323d251378
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863605"
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
