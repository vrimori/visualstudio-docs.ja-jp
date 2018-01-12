---
title: "方法: プログラムによって Word の検索オプションを設定 |Microsoft ドキュメント"
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa575f8c89e9aea125179c896c35b8ecc775965e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>方法: プログラムによって Word の検索オプションを設定する
  これには Microsoft Office Word ドキュメントで選択内容の検索オプションを設定する 2 つの方法があります。  
  
-   個々 のプロパティの設定、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
-   引数を使用して、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Find オブジェクトのプロパティの使用  
 次のコードのプロパティを設定する、<xref:Microsoft.Office.Interop.Word.Find>オブジェクトの現在の選択範囲内のテキストを検索します。 プロパティに、検索するには、転送の折り返し、およびテキストを検索するなど、検索条件が、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト。  
  
 それぞれのプロパティの設定、<xref:Microsoft.Office.Interop.Word.Find>オブジェクト役に立ちますいないでパラメーターとして、同じプロパティを指定する必要がありますので、c# コードを記述するときに、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>メソッドです。 そのためこの例には、Visual Basic コードのみが含まれています。  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Find オブジェクトを使用して検索オプションを設定するには  
  
1.  プロパティを設定、<xref:Microsoft.Office.Interop.Word.Find>のテキスト選択範囲を前方に検索するオブジェクト**find me」**です。  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>メソッドの引数を使用すると実行  
 次のコードでは、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Find>オブジェクトの現在の選択範囲内のテキストを検索します。 パラメーターとして渡されるを検索するには、転送の折り返し、およびテキストを検索するなど、検索条件に注意してください、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>メソッドです。  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Execute メソッドの引数を使用して検索オプションを設定するには  
  
1.  検索条件のパラメーターとして渡す、<xref:Microsoft.Office.Interop.Word.Find.Execute%2A>のテキスト選択範囲を前方に検索するメソッド**find me」**です。  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって検索し、文書内のテキストを置換](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [方法: 文書で見つかった項目をプログラムによってループ](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [方法: プログラムによって検索後に選択範囲を復元する](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  