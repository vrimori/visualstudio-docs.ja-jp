---
title: "Windows ランタイム API を使用する場合の考慮事項 | Microsoft Docs"
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
  - "JavaScript, Windows ランタイム API"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows ランタイム API を使用する場合の考慮事項
JavaScript で Windows ランタイム API のほぼすべての要素をしようできます。  ただし、Windows ランタイム要素の JavaScript 表現には、考慮が必要な面があります。  
  
> [!IMPORTANT]
>  C\+\+、C\#、または Visual Basic での Windows ランタイム コンポーネントの作成について、および JavaScript での利用については、「[Windows ランタイム コンポーネントの作成](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133)」を参照してください。  
  
## Windows ランタイム型の JavaScript 表現の特殊なケース  
  
-   文字列: 初期化されていない文字列は "undefined" 文字列として Windows ランタイム メソッドに渡され、`null` に設定された文字列は "null" 文字列として渡されます \(これは `null` または `undefined` の値が文字列に強制される場合は常に当てはまります\)。Windows ランタイム メソッドに文字列を渡す前に、空の文字列 \(""\) として初期化する必要があります。  
  
-   インターフェイス: JavaScript で Windows ランタイム インターフェイスを実装することはできません。  
  
-   配列: Windows ランタイム配列のサイズは変更できないので、JavaScript で配列のサイズを変更するメソッドは Windows ランタイム配列では機能しません。  
  
-   配列: Windows ランタイム メソッドに JavaScript の配列の値を渡すと、配列がコピーされます。  Windows ランタイム メソッドは、配列またはそのメンバーを変更したり、それを JavaScript アプリに返したりすることはできません。  ただし、コピーされていない型指定された配列 \([Int32Array オブジェクト](../javascript/reference/int32array-object.md) など\) は使用できます。  
  
-   構造体: Windows ランタイム構造体は JavaScript 内のオブジェクトです。  Windows ランタイム メソッドに Windows ランタイム構造体を渡す場合は、`new` キーワードを持つ構造体をインスタンス化しないでください。  その代わりに、オブジェクトを作成し、関連するメンバーとその値を追加します。  メンバー名は Camel 形式 \(`SomeStruct.firstMember`\) でなければなりません。  
  
-   オブジェクト: JavaScript オブジェクトは、マネージ コード オブジェクト \(`System.Object`\) と同じではありません。  `System.Object` を必要とする Windows ランタイム メソッドに JavaScript オブジェクトを渡すことはできません。  
  
-   オブジェクト ID: ほとんどの場合、Windows ランタイムと JavaScript の間でやり取りされるオブジェクトは変更されません。  JavaScript エンジンは既知のオブジェクトのマップを保持します。  オブジェクトが Windows ランタイムから返されると、そのオブジェクトがマップと照合され、そのオブジェクトが存在しない場合は、新しいオブジェクトが作成されます。  Windows ランタイム メソッドによって返されるインターフェイスを表すオブジェクトについても、同様の手順が取られます。  2 種類の例外があります。  
  
    -   Windows ランタイム呼び出しから返されて新しい \(expando\) プロパティが追加されたオブジェクトは、Windows ランタイムに返されるときに新しいプロパティを保持できません。  ただし、JavaScript アプリに返される場合は、既存のオブジェクトに一致するので、返されるオブジェクトは expando プロパティを持ちます。  
  
    -   Windows ランタイムの構造体とデリゲートは、以前に使用した構造体またはデリゲートと同じものとして識別することはできません。  構造体またはデリゲートが返されるたびに、新しい参照を取得します。  
  
-   名前の競合: 複数の Windows ランタイム インターフェイスには、同じ名前のメンバーがある場合があります。  これらが単一の JavaScript オブジェクト内で組み合わされる場合 \(ランタイム クラスまたはインターフェイスの表現である場合もある\)、メンバーは完全修飾名で表されます。  `Class["MemberName"](parameter)` という構文を使用して、これらのメンバーを呼び出すことができます。  
  
     次のコードでは、2 つのインターフェイスに描画メソッドがあり、ランタイム クラスは両方のインターフェイスを実装します。  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     ここで、JavaScript で上記のコードを呼び出します。  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` パラメーター: Windows ランタイム メソッドに複数の `out` パラメーターがある場合、JavaScript では、メソッドは戻り値として JavaScript オブジェクトを持ち、オブジェクトは `out` パラメーターに対応するプロパティを持ちます。  たとえば、C\+\+ で次の Windows ランタイム シグネチャを検討します。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     このシグネチャの JavaScript バージョンは次のとおりです。  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     この例では、`returnValue` は、`first` と `second` の 2 つのフィールドを持つ JavaScript オブジェクトです。  
  
-   静的メンバー: Windows ランタイムは静的メンバーとインスタンス メンバーの両方を定義します。  JavaScript では、静的メンバーは、Windows ランタイム クラスまたはインターフェイスに関連付けられたオブジェクトに追加されます。  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Windows ランタイムの基本型の JavaScript 表現の詳細については、「[Windows ランタイム型の JavaScript 表現](../jswinrt/javascript-representation-of-windows-runtime-types.md)」を参照してください。