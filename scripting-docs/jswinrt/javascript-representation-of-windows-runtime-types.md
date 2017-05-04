---
title: "Windows ランタイム型の JavaScript 表現 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows ランタイム型 [JavaScript]"
  - "JavaScript、Windows ランタイム型"
ms.assetid: f4851802-8b40-4afa-ba6c-8a162a9a43cc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Windows ランタイム型の JavaScript 表現
次の表では、JavaScript で Windows ランタイム型がどのように表現されるかについて説明します。  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## JavaScript での Windows ランタイム型  
  
|Windows ランタイム型|JavaScript での表現|説明|  
|--------------------|---------------------|--------|  
|`UInt8`|`Number`|Windows ランタイムの `Uint8` は、JavaScript の数値として表現される符号なし 8 ビット整数です。  JavaScript の値は、JavaScript の数値に変換されてから、`ToUint32` のプロセスに従います。  JavaScript の数値が Uint8 の範囲外にある場合、結果にはモジュロ 2^8 が適用されます。|  
|`Int32`|`Number`|Windows ランタイムの `Int32` は、JavaScript の数値として表現される符号付き 32 ビット整数です。  JavaScript の値は、JavaScript の数値に変換されてから、`ToInt32` のプロセスに従います。  JavaScript の数値が `Int32` の範囲外にある場合、結果にはモジュロ 2^16 が適用されます。|  
|`Int64`|`Number`|Windows ランタイムの `Int64` が \[\-2^53, 2^53\] の範囲内にある場合、標準数値として表現される符号付き 64 ビット整数になります。  この範囲外になる場合は、整数データの完全な 64 ビットを保持するカスタム バッキング ストアを持つ数値で表現されます。  このようなカスタム Int64 数値に対するすべての数値演算では、値が \[\-2^53, 2^53\] の範囲の標準数値に変換されます。  値がこの範囲外にある場合は、型のエラーが発生します。  この変換プロセスの例外は、`==`、`===`、`SameValue`、および `RelationalComparison` 演算です。これらは 2 つの 64 ビット値が渡されたときに完全な 64 ビットに基づいて引数を比較します。  どちらかの引数が JavaScript の標準数値である場合、これらの演算では比較を行う前に引数が JavaScript の数値に変換されます。  JavaScript の値が Int64 値の場合は、それが直接割り当てられます。それ以外の場合は、`ToInteger` 変換を値に適用した結果が Windows ランタイムに渡されます。  強制型変換に失敗すると、例外が返されます。|  
|`Uint64`|`Number`|Windows ランタイムの `Uint64` が \[0, 2^53\] の範囲内にある場合、標準数値として表現される符号なし 64 ビット整数になります。  この範囲外になる場合は、符号なし整数データの完全な 64 ビットを保持するカスタム バッキング ストアを持つ数値で表現されます。  これらのカスタム Uint64 数値に対するすべての数値演算では、値が \[0, 2^53\] の範囲の標準数値に変換されます。  値がこの範囲外にある場合は、型のエラーが発生します。  この変換プロセスの例外は、`==`、`===`、`SameValue`、および `RelationalComparison` 演算です。これらは 2 つの 64 ビット値が渡されたときに完全な 64 ビットに基づいて引数を比較します。  どちらかの引数が JavaScript の標準数値である場合、これらの演算では比較を行う前に引数が JavaScript の数値に変換されます。  JavaScript の値が Uint64 値の場合は、それが直接割り当てられます。それ以外の場合は、`ToInteger` 変換を値に適用し、モジュロ 2^52 を使用した結果が Windows ランタイムに渡されます。  型の変換に失敗すると、例外が返されます。|  
|`Single`|`Number`|Windows ランタイムの `Single` は、単精度値に最も近い倍精度値を選択することによって JavaScript の数値として表現される 32 ビット浮動小数点数です。  JavaScript の値は、JavaScript の数値に変換された後、単精度 32 ビット IEEE 754 浮動小数点数で表現できるように範囲がチェックされます。  変換または範囲のチェックに失敗すると、マーシャリングのエラーが返されます。|  
|`Double`|`Number`|Windows ランタイムの `Double` は 64 ビット浮動小数点数です。  `ToNumber` が、Windows ランタイムの `Double` を JavaScript の数値に変換するために使用されます。  変換に失敗すると、マーシャリングのエラーが返されます。|  
|`Boolean`|`Boolean`|Windows ランタイムの `Boolean` は、ゼロが `false` で、ゼロ以外の値が `true` である場合に JavaScript の `Boolean` として表現される 8 ビット値です。  JavaScript の値はまず、`ToBoolean` によって JavaScript の `Boolean` に変換されます。  これは `void func(BOOL);` として宣言された Windows ランタイム関数が `obj.func("test");` として JavaScript で記述できることを意味します。  Windows ランタイム関数は `TRUE` として渡された `BOOL` パラメーターと共に呼び出されます。  変換に失敗すると、マーシャリングのエラーが返されます。|  
|`Char16`|`String`|Windows ランタイムの `Char16` は、単一の文字を含む JavaScript 文字列として表現される 16 ビット Unicode 文字です。  JavaScript の値は `ToString` によって JavaScript の文字列に変換された後、文字列の長さが 1 文字であることが確認されます。  単一の文字は `Char16` の値として渡されます。  変換または長さのチェックに失敗すると、マーシャリングのエラーが返されます。|  
|`String`|`String`|Windows ランタイムの `String` は、`Char16` オブジェクトの不変シーケンスです。  文字列は JavaScript の `String` オブジェクトとして表現されます。  Windows ランタイムの文字列では `null` と空の文字列 \(""\) に異なる値はありません。  `null` と空の文字列の値は、JavaScript の空の文字列に変換されます。  メモ: JavaScript の `null` が文字列を想定する Windows ランタイムのパラメーターに渡されると、`null` または空の文字列 \(""\) ではなく、文字列値 "null" が生成されます。  Windows ランタイムに渡される文字列は、常に空の文字列にインスタンス化されます。|  
|`Enumeration`|`Object`|Windows ランタイムの `Enumeration` は、一連の名前付き定数を持つ 32 ビット整数 \(符号付きまたは符号なし\) です。  JavaScript では、列挙型は、それぞれの名前の値に読み取り専用フィールドを含むオブジェクトとして表されます。  列挙型の値は、`Int32` と `UInt32` 用に定義されている JavaScript 数値に変換されます。  JavaScript 値が Windows ランタイムの列挙型に変換されると、前述のように変換、短縮、範囲のチェックが行われます。  ただし、結果の値は、列挙体で定義されている名前付きの値に対してはチェックされません。|  
|`Structure`|`Object`|Windows ランタイムの `Structure` は、名前付きデータ フィールドの異種コレクションです。  JavaScript では、構造体は、構造体の各フィールドの名前付きプロパティを含む JavaScript オブジェクトとして表されます。  構造値の変換に失敗すると、マーシャリングのエラーが返されます。  Windows ランタイムの構造体に同等のものがない JavaScript オブジェクト内のフィールドは無視されます。  メモ: Windows ランタイムの構造体は、JavaScript 内で `new` キーワードでインスタンス化することはできません。|  
|`Array`|`Array`|Windows ランタイムの `Array` は JavaScript 配列に変換されます。  ただし、Windows ランタイム配列のサイズは変更できないので、一部の JavaScript 配列演算は実行できません。  変換された配列の内部 \[\[Class\]\] プロパティは、ECMAScript 5 の仕様によって許可されないため、"Array" に設定されません。  これは、`Array.isArray(v)` が `false` を返すことを意味します。  JavaScript 値は、次のように Windows ランタイムの配列に変換されます。値が `null` または `undefined` の場合、ネイティブの `null` に変換されます。  内部 \[\[Class\]\] プロパティが "Array" の場合は、ネイティブの配列にコピーされ、この配列への参照が渡されます。  変換された配列の場合は、前に説明したように、基になるネイティブの配列が渡されます。  メモ: Windows ランタイム メソッドに JavaScript の配列の値を渡すと、配列がすべてコピーされます。|  
|デリゲート \(関数のコールバック\)|`Function`|Windows ランタイムのデリゲートは単一メソッドへの参照です。  Windows ランタイムのデリゲートは JavaScript の `Function` として JavaScript で表現され、適切なスレッドで呼び出されることが保証されます。  `Function` が呼び出されると、引数は同等の Windows ランタイム パラメーター型に変換されます。  JavaScript の引数が `in` パラメーターより少ない場合、デリゲートの呼び出しは失敗します。  デリゲートの `in` パラメーターより JavaScript の引数が多い場合、JavaScript の余分な引数は無視されます。  デリゲートが呼び出された後、`out` パラメーターは JavaScript の型に変換されて返されます。  ネイティブの JavaScript 関数オブジェクトが Windows ランタイムのデリゲートに変換されると、対応する型の Windows ランタイム型でラップされます。  デリゲートが呼び出されると、`in` パラメーターは JavaScript の型に変換されます。  デリゲートが呼び出された後、戻り値はデリゲートの `out` パラメーターに変換されます。|  
|インターフェイス|`Object`|インターフェイスとインターフェイス グループは、オブジェクトとして JavaScript で直接表現されることはありません。  ただし、インターフェイスは、Windows ランタイム メソッドのパラメーターと戻り値の型として表されます。  Windows ランタイム インターフェイスのインスタンスは、次のように変換されます。<br /><br /> 1.  有効なランタイム クラスがある場合は、そのクラスのインスタンスとしてオブジェクトを表します。<br />2.  有効なランタイム クラスがない場合は、インスタンスで実装されることが知られているインターフェイスおよび必要なインターフェイスを正確に実装する名前のないランタイム クラスのインスタンスとしてオブジェクトを表します。<br /><br /> JavaScript の値は、ランタイム クラスまたはインターフェイスのインスタンスであるかどうかがテストされます。  インスタンスであり、元の Windows ランタイム値がインターフェイスを実装する場合、オブジェクトは Windows ランタイムに渡されます。|  
|ランタイム クラス|`Object`|Windows ランタイムのオブジェクトは、1 つ以上のインターフェイスを実装するランタイム クラスのインスタンスにすることができます。  Windows ランタイムのオブジェクトは、JavaScript でオブジェクトとして表現されます。  クラスのすべての実装済みインターフェイスで定義されているメソッド、プロパティ、およびイベントの共用体は、JavaScript オブジェクトのプロトタイプの名前付きプロパティを表します。  JavaScript のコンシューマーは、どのクラス メンバーにでも直接アクセスできます。  Windows ランタイム オブジェクトは、ランタイム クラスのすべての実装済みインターフェイスのすべてのメンバーを含むプロトタイプを持ちます。|  
  
## 参照  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)