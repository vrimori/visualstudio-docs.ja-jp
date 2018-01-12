---
title: "方法: プログラムによってブックとしてテキスト ファイルを開く |Microsoft ドキュメント"
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
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 45d2b85ea8c005d56ddc076d0b758a0c9e4a2d67
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>方法: プログラムによってテキスト ファイルをブックとして開く
  ブックとしてテキスト ファイルを開くことができます。 開きたいテキスト ファイルの名前を渡す必要があります。 ファイル内のデータの列の形式、解析を開始する行番号など、いくつかの省略可能なパラメーターを指定することができます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>例  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、次のコンポーネントが必要です。  
  
-   という名前のコンマ区切りのテキスト ファイル`Test.txt`少なくとも 3 つの行のテキストを格納しています。  
  
-   テキスト ファイル`Test.txt`C ドライブに保存します。  
  
## <a name="see-also"></a>参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)   
 [方法: プログラムによって新しいブックを作成します。](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [方法: プログラムによってブックを保存](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  