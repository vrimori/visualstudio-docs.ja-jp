---
title: "GetObject 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject 関数"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject 関数 (JavaScript)
ファイルのオートメーション オブジェクトへの参照を返します。  
  
> [!NOTE]
>  この関数は、Internet Explorer 9 \(標準モード\) 以降ではサポートされていません。  
  
## 構文  
  
```  
GetObject([pathname] [, class])  
```  
  
## Parameters  
 `pathname`  
 Optional.  オブジェクトが含まれているファイル名までの完全パスを指定します。  `pathname` を省略した場合、`class` が必須になります。  
  
 `class`  
 Optional.  オブジェクトのクラスを指定します。  
  
 `class` 引数は、`appname.objectype` 構文を使用します。各部を次に示します。  
  
 `appname`  
 Required.  オブジェクトを提供するアプリケーションの名前です。  
  
 `objectype`  
 Required.  作成するオブジェクトの型またはクラスです。  
  
## 解説  
 `GetObject` 関数は、[!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 以降ではサポートされていません。  
  
 ファイルのオートメーション オブジェクトにアクセスし、オブジェクトをオブジェクト変数に代入するには、`GetObject` 関数を使用します。  `GetObject` 関数で返されるオブジェクトへの参照をオブジェクト変数に代入します。  次に例を示します。  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 このコード例が実行されると、指定された引数 `pathname` に対応するアプリケーションが起動し、指定されたファイルのオブジェクトがアクティブになります。  `GetObject` は、引数 `pathname` に長さ 0 の文字列 \(""\) が指定されると、指定した型の新しいオブジェクト インスタンスを返します。  引数 `pathname` を省略すると、`GetObject` は、指定した型の現在アクティブなオブジェクトを返します。  指定した種類のオブジェクトが存在しない場合はエラーが発生します。  
  
 アプリケーションによっては、ファイルの一部をアクティブにできる場合もあります。  ファイル名の最後に感嘆符 \(\!\) を付け、続けてアクティブにするファイルの部分を表す文字列を指定します。  この文字列を作成する方法については、オブジェクトを作成したアプリケーションのドキュメントを参照してください。  
  
 たとえば、描画アプリケーションでファイルに格納されている画像に複数のレイヤーが含まれているとします。  次のコードを使用すると、`SCHEMA.CAD` という描画ファイルの 1 つのレイヤーをアクティブにできます。  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 オブジェクトのクラスが指定されていない場合は、指定されたファイル名を基に、オートメーションは起動するアプリケーションとアクティブにするオブジェクトを決定します。  ただし、ファイルによっては、複数のオブジェクトのクラスをサポートしている場合もあります。  たとえば、1 つの描画で Application オブジェクト、Drawing オブジェクト、および Toolbar オブジェクトという 3 つの異なる種類のオブジェクトを同一ファイルの構成要素としてサポートすることもあります。  ファイルのどのオブジェクトをアクティブにするかは、引数 `class` で指定します。  次に例を示します。  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 このコード例では、`FIGMENT` が描画のアプリケーションの名前で、`DRAWING` がそのアプリケーションによってサポートされるオブジェクトの種類です。  アクティブになったオブジェクトをコードで参照するには、定義したオブジェクト変数を使います。  上の例では、オブジェクト変数 `MyObject` を使って新規オブジェクトのプロパティとメソッドにアクセスします。  次に例を示します。  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  `GetObject` 関数は、オブジェクトの現在のインスタンスがある場合や、既に読み込んだファイルからオブジェクトを作成する場合に使います。  現在のインスタンスがない場合、または読み込み済みのファイルからオブジェクトを起動しない場合は、`ActiveXObject` オブジェクトを使います。  
  
 複数のインスタンスを作成できないオブジェクトの場合は、何度 `ActiveXObject` 関数を実行しても、そのオブジェクトのインスタンスは 1 つしか作成されません。  単一インスタンス オブジェクトの場合、引数に長さ 0 の文字列 \(""\) を指定して `GetObject` を呼び出すと、常に同じインスタンスを返します。また、引数 `pathname` を省略すると、エラーになります。  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準の各ドキュメント モードでサポートされます。  「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
## 参照  
 [ActiveXObject オブジェクト](../../javascript/reference/activexobject-object-javascript.md)