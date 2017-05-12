---
title: "Office ソリューションの省略可能なパラメーター"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アプリケーション開発 [Visual Studio での Office 開発], 省略可能なパラメーター"
  - "存在しないフィールド [Visual Studio での Office 開発]"
  - "Office アプリケーション [Visual Studio での Office 開発], 省略可能なパラメーター"
  - "省略可能なパラメーター [Visual Studio での Office 開発]"
  - "パラメーター [Visual Studio での Office 開発], optional"
  - "Visual Basic [Visual Studio での Office 開発], 省略可能なパラメーター"
  - "Visual C# [Visual Studio での Office 開発], 省略可能なパラメーター"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Office ソリューションの省略可能なパラメーター
  Microsoft Office アプリケーションのオブジェクト モデルに含まれるメソッドの多くは、省略可能なパラメーターを受け取ります。  Visual Studio で Visual Basic を使用して Office ソリューションを開発する場合は、省略可能なパラメーターに値を渡す必要はありません。省略したパラメーターに対しては自動的に既定値が使用されます。  ほとんどの場合は、Visual C\# プロジェクトでも省略可能なパラメーターを省略できます。 ただし、ドキュメント レベルの Word プロジェクトでは、**ref** クラスの `ThisDocument` の省略可能なパラメーターは省略できません。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual C\# および Visual Basic プロジェクトで省略可能なパラメーターを使用する詳細については、「[名前付き引数と省略可能な引数 &#40;C&#35; プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments)」および「[Optional Parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)」を参照してください。  
  
> [!NOTE]  
>  旧バージョンの Visual Studio では、Visual C\# プロジェクトのすべての省略可能なパラメーターに値を渡す必要があります。  便宜上、これらのプロジェクトには `missing` というグローバル変数が含まれています。パラメーターの既定値を使用する場合に、このグローバル変数を省略可能なパラメーターに渡すことができます。  Visual Studio の Office の Visual C\# プロジェクトにも `missing` 変数が含まれていますが、通常、[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] で Office ソリューションを開発する場合は、この変数を使用する必要はありません。ただし、ドキュメント レベルの Word プロジェクトで、省略可能な **ref** パラメーターを持つ `ThisDocument` クラスのメソッドを呼び出す場合は例外です。  
  
## Excel の例  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> メソッドには、多くの省略可能なパラメーターがあります。  次のコード例に示すように、一部のパラメーターの値を指定し、他のパラメーターには既定値を使用することができます。  この例では、`Sheet1` というワークシート クラスを持つドキュメント レベルのプロジェクトが必要です。  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Word の例  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> メソッドには、多くの省略可能なパラメーターがあります。  次のコード例に示すように、一部のパラメーターの値を指定し、他のパラメーターには既定値を使用することができます。  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Word 用の Visual C\# ドキュメント レベル プロジェクトの ThisDocument クラスでのメソッドの省略可能なパラメーターの使用  
 Word オブジェクト モデルには、**ref** 値を使用する省略可能な <xref:System.Object> パラメーターを持つメソッドが多数あります。  しかし、Word 用の Visual C\# ドキュメント レベル プロジェクトでは、生成された **ref** クラスのメソッドの省略可能なパラメーター `ThisDocument` を省略できません。  Visual C\# では、クラスではなくインターフェイスのメソッドについてのみ、省略可能な **ref** パラメーターを省略できます。  たとえば、次のコード例ではコンパイルしません。これは、**ref** クラスの <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> メソッドの省略可能な `ThisDocument` パラメーターを省略できないためです。  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 `ThisDocument` クラスのメソッドを呼び出す場合は、次のガイドラインに従います。  
  
-   省略可能な **ref** パラメーターの既定値を使用するには、パラメーターに `missing` 変数を渡します。  `missing` 変数は Visual C\# Office プロジェクトで自動的に定義され、生成されたプロジェクト コード内で <xref:System.Type.Missing> 値に割り当てられます。  
  
-   省略可能な **ref** パラメーターに独自の値を指定するには、指定する値に割り当てられるオブジェクトを宣言し、オブジェクトをパラメーターに渡します。  
  
 次のコード例は、<xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> パラメーターの値を指定し、他のパラメーターの既定値を受け入れることで *ignoreUppercase* メソッドを呼び出す方法を示しています。  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 **ref** クラスのメソッドの省略可能な `ThisDocument` パラメーターを省略するコードを記述するには、別の方法として、<xref:Microsoft.Office.Interop.Word.Document> プロパティから返される <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> オブジェクトの同じメソッドを呼び出し、そのメソッドのパラメーターを省略することができます。  これは、<xref:Microsoft.Office.Interop.Word.Document> がクラスではなくインターフェイスであるためです。  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 値型と参照型のパラメーターの詳細については、「[Passing Arguments by Value and by Reference &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)」 \(Visual Basic の場合\) および「[パラメーターの引き渡し &#40;C&#35; プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)」参照してください。  
  
## 参照  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)  
  
  