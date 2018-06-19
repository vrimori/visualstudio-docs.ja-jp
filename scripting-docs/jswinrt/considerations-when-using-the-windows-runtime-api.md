---
title: Windows ランタイム API を使用する際の考慮事項 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571472"
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Windows ランタイム API を使用する際の考慮事項
JavaScript では Windows ランタイム API のほぼすべての要素を使用することができます。 ただし、Windows ランタイム要素の JavaScript 表現には、覚えておかなければならない側面がいくつかあります。  
  
> [!IMPORTANT]
>  C++、C#、または Visual Basic での Windows ランタイム コンポーネントの作成と JavaScript での使用方法については、「[C++ で Windows ランタイム コンポーネントを作成する](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)」および「[C++ および Visual Basic での Windows ランタイム コンポーネントの作成](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)」を参照してください。  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Windows ランタイム型の JavaScript 表現の特殊なケース  
  
-   文字列: 初期化されていない文字列が文字列 "undefined" として Windows ランタイム メソッドに渡され、`null` に設定された文字列が文字列 "null" として渡されます。 (これは、`null` または `undefined` の値が文字列に強制されている場合、常に該当します。)文字列を Windows ランタイム メソッドに渡す前に、文字列を空の文字列 ("") として初期化する必要があります。  
  
-   インターフェイス: JavaScript では Windows ランタイム インターフェイスを実装できません。  
  
-   配列: Windows ランタイムの配列のサイズを変更できないため、JavaScript で配列のサイズを変更するメソッドが Windows ランタイムの配列で機能しません。  
  
-   配列: Windows ランタイム メソッドに JavaScript の配列の値を渡すと、配列がコピーされます。 Windows ランタイム メソッドは、配列またはそのメンバーを変更して JavaScript アプリに戻すことはできません。 ただし、コピーされない、型指定された配列 (たとえば、[Int32Array オブジェクト](../javascript/reference/int32array-object.md)) は使用できます。  
  
-   構造体: Windows ランタイムの構造体は JavaScript のオブジェクトです。 Windows ランタイムの構造体を Windows ランタイム メソッドに渡す場合、`new` キーワードで構造体を初期化しないでください。 代わりに、オブジェクトを作成して、関連するメンバーとその値を追加します。 メンバーの名前はキャメル ケース (`SomeStruct.firstMember`) にする必要があります。  
  
-   オブジェクト: JavaScript オブジェクトはマネージ コード オブジェクト (`System.Object`) と同じではありません。 `System.Object` を必要とする Windows ランタイム メソッドに JavaScript オブジェクトを渡すことはできません。  
  
-   オブジェクト ID: ほとんどの場合、Windows ランタイムと JavaScript の間で受け渡しが行われるオブジェクトは変更されません。 JavaScript エンジンは、既知のオブジェクトのマップを保持します。 Windows ランタイムから戻されたオブジェクトはマップと照合され、マップに存在しない場合には新しいオブジェクトが作成されます。 Windows ランタイム メソッドによって戻されるインターフェイスを表すオブジェクトでも同じ手順が実行されます。 次の 2 つの例外があります。  
  
    -   Windows ランタイムの呼び出しから戻されたオブジェクトには新しい (expando) プロパティが追加されますが、これらの新しいプロパティは、Windows ランタイムに戻されたときに保持されません。 ただし、JavaScript アプリに戻された場合、オブジェクトが既存のオブジェクトと一致するため、戻されたオブジェクトに expando プロパティが含まれます。  
  
    -   Windows ランタイムの構造体とデリゲートは、以前に使用された構造体やデリゲートと同一であると識別できません。 構造体やデリゲートが戻されるたびに、新しい参照が取得されます。  
  
-   名前の競合: 複数の Windows ランタイム インターフェイスに同じ名前のメンバーが含まれる可能性があります。 単一の JavaScript オブジェクト (ランタイム クラスまたはインターフェイスの表現である場合があります) と組み合わされると、メンバーは完全修飾名で表現されます。 これらのメンバーは `Class["MemberName"](parameter)` の構文を使用して呼び出すことができます。  
  
     次のコードでは、2 つのインターフェイスに Draw メソッドが含まれ、ランタイム クラスは両方のインターフェイスを実装します。  
  
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
  
     JavaScript で上記のコードを呼び出す方法を示します。  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   `Out` パラメーター: Windows ランタイム メソッドに複数の `out` パラメーターがある場合、JavaScript ではメソッドの戻り値として JavaScript オブジェクトが含まれ、そのオブジェクトには `out` パラメーターに対応するプロパティが含まれます。 たとえば、C++ で次の Windows ランタイム シグネチャについて考えてみます。  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     このシグネチャの JavaScript のバージョンは次のようになります。  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     この例では、`returnValue` は `first` と `second` の 2 つのフィールドを持つ JavaScript オブジェクトです。  
  
-   静的メンバー: Windows ランタイムは、静的メンバーとインスタンス メンバーの両方を定義します。 JavaScript では、Windows ランタイム クラスまたはインターフェイスに関連するオブジェクトに静的メンバーが追加されます。  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Windows ランタイムの基本型の JavaScript 表現の詳細については、「[JavaScript Representation of Windows Runtime Types](../jswinrt/javascript-representation-of-windows-runtime-types.md)」(Windows ランタイム型の JavaScript 表現) を参照してください。