---
title: "グローバリゼーションの警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.globalizationrules"
helpviewer_keywords: 
  - "グローバリゼーション [Visual Studio], 警告"
  - "グローバリゼーションに関する警告"
  - "マネージ コード分析の警告, グローバリゼーションに関する警告"
  - "警告, グローバリゼーション"
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# グローバリゼーションの警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グローバリゼーションの警告は、国際対応のライブラリとアプリケーションをサポートします。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA1300: MessageBoxOption を指定します](../code-quality/ca1300-specify-messageboxoptions.md)|テキストを右から左へ読むカルチャでメッセージ ボックスを正しく表示するには、MessageBoxOptions 列挙体の RightAlign メンバーと RtlReading メンバーを、Show メソッドに渡す必要があります。|  
|[CA1301: アクセラレータが重複しないようにします](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Alt キーを使用するアクセス キー \(アクセラレータとも呼ばれます\) によって、キーボードからコントロールにアクセスできます。  アクセス キーの重複したコントロールがあると、アクセス キーの動作は不明確になります。|  
|[CA1302: ロケール特有の文字列をハードコードしません](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|System.Environment.SpecialFolder 列挙体には、特殊なシステム フォルダーを参照するメンバーが含まれます。  このフォルダーの位置は、オペレーティング システムによって異なる場合、ユーザーが位置を変更する場合、および位置がローカライズされる場合があります。  Environment.GetFolderPath メソッドは、Environment.SpecialFolder 列挙体に関連付けられ、ローカライズされ、現在実行されているコンピューターに適切な位置を返します。|  
|[CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|外部から参照できるメソッドが、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] クラス ライブラリのコンストラクターまたはメソッドへのパラメーターとして、リテラル文字列を渡しています。その文字列はローカライズ可能です。|  
|[CA1304: CultureInfo を指定します](../Topic/CA1304:%20Specify%20CultureInfo.md)|System.Globalization.CultureInfo パラメーターを受け入れるオーバーロードを持つメンバーを呼び出しているメソッドまたはコンストラクターが、CultureInfo パラメーターを使用するオーバーロードを呼び出していません。  CultureInfo オブジェクトまたは System.IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。|  
|[CA1305: IFormatProvider を指定します](../code-quality/ca1305-specify-iformatprovider.md)|System.IFormatProvider パラメーターを受け入れるオーバーロードを持つメンバーを 1 つ以上呼び出しているメソッドまたはコンストラクターが、IFormatProvider パラメーターを使用するオーバーロードを呼び出していません。  System.Globalization.CultureInfo オブジェクトまたは IFormatProvider オブジェクトが指定されない場合、オーバーロードされたメンバーから提示された既定値は、すべてのロケールに効果が及ばない可能性があります。|  
|[CA1306: データ型のロケールを設定します](../code-quality/ca1306-set-locale-for-data-types.md)|ロケールによって、データに関するカルチャ固有の表示要素が決まります。たとえば、数値、通貨記号、並べ替え順序に使用する形式などです。  DataTable または DataSet を作成するときは、ロケールを明示的に設定する必要があります。|  
|[CA1307: StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)|文字列比較演算で、StringComparison パラメーターを設定しないメソッド オーバーロードが使用されています。|  
|[CA1308: 文字列を大文字に標準化します](../code-quality/ca1308-normalize-strings-to-uppercase.md)|文字列は大文字に正規化する必要があります。  小文字への変換時に 1 つの小さい文字グループをラウンド トリップさせることができません。|  
|[CA1309: 順序を示す StringComparison を使用します](../code-quality/ca1309-use-ordinal-stringcomparison.md)|非言語的な文字列比較演算で、StringComparison パラメーターが Ordinal または OrdinalIgnoreCase に設定されていません。  パラメーターを StringComparison.Ordinal または StringComparison.OrdinalIgnoreCase に明示的に設定することによって、多くの場合、コードの速度、正確さ、および信頼性が向上します。|  
|[CA2101: P\/Invoke 文字列引数に対してマーシャリングを指定します](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|プラットフォーム呼び出しメンバーが、部分信頼の呼び出し元を許可し、文字列パラメーターを持ち、さらにその文字列を明示的にマーシャリングしていません。  これはセキュリティ上の脆弱性となる可能性があります。|