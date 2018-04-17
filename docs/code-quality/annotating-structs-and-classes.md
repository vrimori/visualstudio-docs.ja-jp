---
title: 構造体とクラスに注釈を付ける |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2735ae7ba6763a3006edce146df1b19cbaed2f2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="annotating-structs-and-classes"></a>構造体とクラスに注釈を付ける
不変式のように動作する注釈を使用して、構造体とクラスのメンバーに注釈を付けることができます: これらは任意の関数呼び出しまたは関数の開始/終了パラメーターまたは結果の値として、囲み構造を含むで true であると見なされます。  
  
## <a name="struct-and-class-annotations"></a>構造体とクラスの注釈  
  
-   `_Field_range_(low, high)`  
  
     フィールドは、範囲 (包括) から`low`に`high`です。  等価`_Satisfies_(_Curr_ >= low && _Curr_ <= high)`前または後の適切な条件を使用して注釈付きオブジェクトに適用します。  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     要素 (またはバイト数) としてによって指定された書き込み可能なサイズが使用されているフィールド`size`です。  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     要素 (またはバイト数) としてによって指定された書き込み可能なサイズが使用されているフィールド`size`、および`count`読み取り可能なそれらの要素 (バイト単位)。  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Readable と writable の両方のサイズ要素 (またはバイト数) としてによって指定された単位を持つフィールドを`size`です。  
  
-   `_Struct_size_bytes_(size)`  
  
     Readable と writable の両方のサイズ要素 (またはバイト数) としてによって指定された単位を持つフィールドを`size`です。  
  
     構造体またはクラス宣言に適用されます。  指定されているバイト数とその型の有効なオブジェクトを宣言された型よりも大きいする可能性があることを示します`size`です。  例えば:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        ...  
    };  
  
    ```  
  
     パラメーターのバイト単位のバッファー サイズ`pM`型の`MyStruct *`が作成されるとします。  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>関連項目  
 [C/C++ コード障害を減らす SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL について](../code-quality/understanding-sal.md)   
 [関数パラメーターおよび戻り値の注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md)   
 [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)   
 [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)   
 [注釈を適用するタイミングと場所を指定します。](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [組み込み関数](../code-quality/intrinsic-functions.md)   
 [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)