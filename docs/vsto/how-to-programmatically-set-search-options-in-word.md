---
title: '方法: プログラムによって Word の検索オプションを設定します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec5b2f797371d19fea1b4fedc2064ab355ffac10
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853387"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>方法: プログラムによって Word の検索オプションを設定します。
  Microsoft Office Word 文書で選択内容の検索オプションを設定する 2 つの方法はあります。  
  
- 個々 のプロパティの設定、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
- 引数を使用して、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>のメソッドを<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-properties-of-a-find-object"></a>Find オブジェクトのプロパティを使用します。  
 次のコードのプロパティの設定、<xref:Microsoft.Office.Interop.Word.Find>オブジェクトの現在の選択範囲内のテキストを検索します。 プロパティは、検索するには、順方向、折り返し、およびテキストを検索するなど、検索条件、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
 それぞれのプロパティの設定、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト内のパラメーターとして同じプロパティを指定する必要がありますので、c# コードを記述する場合は役に立ちません、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>メソッド。 したがってこの例には、Visual Basic コードのみが含まれています。  
  
### <a name="to-set-search-options-using-a-find-object"></a>Find オブジェクトを使用して検索オプションを設定するには  
  
1.  プロパティを設定、<xref:Microsoft.Office.Interop.Word.Find>テキスト選択範囲を前方に検索するオブジェクト**検索 me**します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="use-execute-method-arguments"></a>Execute メソッドの引数を使用して、  
 次のコードでは、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>のメソッドを<xref:Microsoft.Office.Interop.Word.Find>オブジェクトの現在の選択範囲内のテキストを検索します。 パラメーターとして渡されるを検索するには、順方向、折り返し、およびテキストを検索するなど、検索条件に注意してください、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>メソッド。  
  
### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute メソッドの引数を使用して、検索オプションを設定するには  
  
1.  パラメーターとしての検索条件を渡す、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>テキスト選択範囲を前方に検索するメソッド**検索 me**します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムを検索して、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [方法: プログラムによって文書で見つかった項目をループします。](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [方法: プログラムによって検索後に選択内容を復元します。](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
