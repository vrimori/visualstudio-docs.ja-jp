---
title: Office ソリューションの省略可能なパラメーター |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d417b5126989736c6126ae7c80bfcbc86f336a09
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="optional-parameters-in-office-solutions"></a>Office ソリューションの省略可能なパラメーター
  Microsoft Office アプリケーションのオブジェクト モデルに含まれるメソッドの多くは、省略可能なパラメーターを受け取ります。 Visual Studio で Visual Basic を使用して Office ソリューションを開発する場合は、省略可能なパラメーターに値を渡す必要はありません。省略したパラメーターに対しては自動的に既定値が使用されます。 ほとんどの場合は、Visual c# プロジェクトで省略可能なパラメーターも省略できます。 ただし、省略することはできませんと省略可能な**ref**のパラメーター、`ThisDocument`ドキュメント レベルの Word プロジェクトのクラスです。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual c# および Visual Basic プロジェクトで省略可能なパラメーターの扱いの詳細については、次を参照してください[名前付き引数と省略可能な引数&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments)と[&#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)です。  
  
> [!NOTE]  
>  旧バージョンの Visual Studio では、Visual C# プロジェクトのすべての省略可能なパラメーターに値を渡す必要があります。 便宜上、これらのプロジェクトには `missing` というグローバル変数が含まれています。パラメーターの既定値を使用する場合に、このグローバル変数を省略可能なパラメーターに渡すことができます。 Visual Studio での Office の visual c# プロジェクトがまだが含まれて、`missing`変数が通常必要はありませんでの Office ソリューションを開発するときに使用する[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]、オプションのメソッドを呼び出す場合を除く**ref**内のパラメーター、 `ThisDocument` Word 用ドキュメント レベルのプロジェクト内のクラスです。  
  
## <a name="example-in-excel"></a>Excel の例  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> メソッドには、多くの省略可能なパラメーターがあります。 次のコード例に示すように、一部のパラメーターの値を指定し、他のパラメーターには既定値を使用することができます。 この例では、`Sheet1` というワークシート クラスを持つドキュメント レベルのプロジェクトが必要です。  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Word の例  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドには、多くの省略可能なパラメーターがあります。 次のコード例に示すように、一部のパラメーターの値を指定し、他のパラメーターには既定値を使用することができます。  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Word 用の Visual C# ドキュメント レベル プロジェクトの ThisDocument クラスでのメソッドの省略可能なパラメーターの使用  
 Word オブジェクト モデルには、多くの方法でオプションが含まれています。 **ref**を受け取るパラメーター<xref:System.Object>値。 ただし、省略することはできませんと省略可能な**ref**生成されるメソッドのパラメーターを`ThisDocument`Visual c# ドキュメント レベルのプロジェクトで Word 用のクラスです。 Visual c# を使用するとオプションを省略する**ref**のみのインターフェイスのメソッドのパラメーターがないクラスです。 たとえば、次のコード例はコンパイルされず、オプションを省略することはできませんので**ref**のパラメーター、<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>のメソッド、`ThisDocument`クラスです。  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 `ThisDocument` クラスのメソッドを呼び出す場合は、次のガイドラインに従います。  
  
-   省略可能な既定値を受け入れるように**ref**パラメーターでは、パス、`missing`変数、パラメーターにします。 `missing` 変数は Visual C# Office プロジェクトで自動的に定義され、生成されたプロジェクト コード内で <xref:System.Type.Missing> 値に割り当てられます。  
  
-   省略可能なため、独自の値を指定する**ref**パラメーターを指定する値に割り当てられているオブジェクトを宣言し、パラメーターに、オブジェクトを渡します。  
  
 次のコード例を呼び出す方法を示しています、<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>メソッドの値を指定することによって、 *ignoreUppercase*パラメーターおよび他のパラメーターの既定値を受け入れることです。  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 省略可能な指定を省略するコードを記述する場合**ref**内のメソッドのパラメーター、`ThisDocument`クラス、または同じメソッドを呼び出せます、<xref:Microsoft.Office.Interop.Word.Document>によって返されるオブジェクト、<xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A>プロパティを省略し、そのメソッドのパラメーターです。 これは、<xref:Microsoft.Office.Interop.Word.Document> がクラスではなくインターフェイスであるためです。  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 値と参照型のパラメーターの詳細については、次を参照してください[値と参照渡しに引数を渡す&#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic の場合) 用と[パラメーターの引き渡し&#40;C&#35; 。プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  