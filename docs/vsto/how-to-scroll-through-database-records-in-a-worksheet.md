---
title: "方法: ワークシート内のデータベース レコードをスクロール |Microsoft ドキュメント"
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
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>方法 : ワークシート内でデータベースのレコードをスクロールする
  次の手順では、デザイナーを使用して、エンドユーザーが、すべてのレコードをスクロールできるようにするコントロールでの Microsoft Office Excel ワークシートに、データベース テーブルから単一のフィールドを表示する方法を示します。  
  
 デザイナーは、ドキュメント レベルのプロジェクトでのみ使用できます。 ただしもコントロールを追加して実行時にデータをプログラムでバインドにします。 詳細については、次を参照してください。[チュートリアル: VSTO での単純データ バインディング アドイン プロジェクト](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)です。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>ワークシート内のデータベース レコードをスクロールするには  
  
1.  Visual Studio で Excel アプリケーション プロジェクトを開きます。  
  
2.  開く、**データソース**ウィンドウ データベースからデータ ソースを作成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。  
  
3.  表示するデータを格納しているテーブルを展開し、特定の列を選択します。  
  
4.  コントロールと選択のリストを開く**NamedRange**です。  
  
5.  ドラッグ、<xref:Microsoft.Office.Tools.Excel.NamedRange>コントロールをデータを表示するセルにします。  
  
6.  **Windows フォーム**のタブ、**ツールボックス**、追加、<xref:System.Windows.Forms.BindingNavigator>ワークシートに制御し、使用するコントロールを設定します。 詳細については、次を参照してください。 [BindingNavigator コントロールの概要 &#40;です。Windows フォーム &#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>参照  
 [Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  