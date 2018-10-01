---
title: 構造体とクラスに注釈を付ける
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
- _Field_z_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: e4294284ff2911fd05cc771bf4deaad368e3c28b
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228826"
---
# <a name="annotating-structs-and-classes"></a>構造体とクラスに注釈を付ける
インバリアントのように動作する注釈を使用して構造体とクラスのメンバーに注釈を付けることができます: これらは true に、関数呼び出し、または関数の開始/終了パラメーターまたは結果の値として外側の構造体を含むと見なされます。

## <a name="struct-and-class-annotations"></a>構造体とクラスの注釈

-   `_Field_range_(low, high)`

     フィールドがから (包括) の範囲である`low`に`high`します。  等価`_Satisfies_(_Curr_ >= low && _Curr_ <= high)`適切なプリトリガーまたは条件を使用して、注釈付きのオブジェクトに適用します。

-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     要素 (またはバイト数) とで指定された書き込み可能なサイズのフィールド`size`します。

-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     要素 (またはバイト数) とで指定された書き込み可能なサイズのフィールド`size`、および`count`は読み取り可能なそれらの要素 (バイト単位)。

-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     読み取りと書き込みの両方のサイズの要素 (またはバイト数) とで指定されたフィールド`size`します。

-   `_Field_z_`

     Null で終わる文字列フィールドです。

-   `_Struct_size_bytes_(size)`

     構造体またはクラスの宣言に適用されます。  指定されているバイト数でその型の有効なオブジェクトを宣言された型よりも大きいでことがあることを示します`size`します。  例えば:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     パラメーターのバイト単位のバッファー サイズ`pM`型の`MyStruct *`が表示されます。

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="see-also"></a>関連項目
 [SAL 注釈を使用して C/C++ のコード障害を減らす](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [SAL を理解する](../code-quality/understanding-sal.md)[関数パラメーターと戻り値に注釈を付ける](../code-quality/annotating-function-parameters-and-return-values.md) [の関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)[ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)[注釈を適用するタイミングと場所を指定する](../code-quality/specifying-when-and-where-an-annotation-applies.md)[組み込み関数](../code-quality/intrinsic-functions.md)[ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)
