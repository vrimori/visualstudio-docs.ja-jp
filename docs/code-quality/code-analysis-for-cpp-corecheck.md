---
title: Visual Studio の C++ コア ガイドライン チェッカー リファレンス
ms.date: 03/22/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6d68ed1d7002ac0e92d3a8c3e32226cb3a38c3f0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="c-core-guidelines-checker-reference"></a>C++ の主要なガイドライン チェッカー参照

このセクションでは、C++ の主要なガイドラインのチェックの警告を一覧表示します。 コード分析の詳細については、次を参照してください。 [/analyze (コード分析)](/cpp/build/reference/analyze-code-analysis)と[クイック スタート: c/c++ コード分析](../code-quality/quick-start-code-analysis-for-c-cpp.md)です。

> [!NOTE]
> いくつかの警告が 2 つ以上のグループに属しているし、すべての警告が完全なリファレンス トピックを持ちます。

## <a name="ownerpointer-group"></a>OWNER_POINTER Group

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) Return a scoped object instead of a heap-allocated if it has a move constructor. 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26403 RESET_OR_DELETE_OWNER](C26403.md)リセットまたは所有者を明示的に削除\<T > ポインターが '% 変数 %' です。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26404 DONT_DELETE_INVALID](C26404.md)所有者を削除しないでください\<T > 無効な状態である可能性があります。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)所有者に割り当てないでください\<T > 有効な状態である可能性があります。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)所有者に生のポインターを割り当てないでください\<T > です。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Prefer scoped objects, don't heap-allocate unnecessarily. 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。

[C26429 USE_NOTNULL](C26429.md)シンボル '% シンボル %' がないことをテストされていません、not_ としてマークできます。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

[C26430 TEST_ON_ALL_PATHS](C26430.md)シンボル '% シンボル %' には、すべてのパスでないことをテストされていません。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

[C26431 DONT_TEST_NOTNULL](C26431.md)式 '%expr% ' の型は、既に gsl::not_null です。 ないことをテストしないでください。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

## <a name="rawpointer-group"></a>RAW_POINTER グループ

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)所有者に割り当て、または関数の呼び出しの結果を割り当てないでください\<T >、生のポインターに値を返します。 所有者を使用して\<T > 代わりにします。 参照してください[C++ コア ガイドライン I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)です。

[C26401 DONT_DELETE_NON_OWNER](c26401.md)所有者ではなく生のポインターを削除しないでください\<T > です。 参照してください[C++ コア ガイドライン I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)です。

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  Return a scoped object instead of a heap-allocated if it has a move constructor. 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。

[C26408 NO_MALLOC_FREE](C26408.md) malloc() および free() を回避するため、削除で新規の nothrow バージョンを使用します。 参照してください[C++ コア ガイドライン R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)です。

[C26409 NO_NEW_DELETE](C26409.md)新しい呼び出しを避けるため、明示的に削除して、std::make_unique を使用して\<T > 代わりにします。 参照してください[C++ コア ガイドライン R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)です。

[C26429 USE_NOTNULL](C26429.md)シンボル '% シンボル %' がないことをテストされていません、not_ としてマークできます。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

[C26430 TEST_ON_ALL_PATHS](C26430.md)シンボル '% シンボル %' には、すべてのパスでないことをテストされていません。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

[C26431 DONT_TEST_NOTNULL](C26431.md)式 '%expr% ' の型は、既に gsl::not_null です。 ないことをテストしないでください。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。

[C26481 NO_POINTER_ARITHMETIC](C26481.md)ポインター演算を使用しません。 スパンを使用してください。 参照してください[C++ コア ガイドライン Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
式 '%expr% ': ポインター減衰にない配列。 参照してください[C++ コア ガイドライン Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。

## <a name="uniquepointer-group"></a>UNIQUE_POINTER Group

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)パラメーター '% パラメーター %' への参照は、`const`一意のポインター、const T * または const T を使用して & 代わりにします。 参照してください[C++ コア ガイドライン R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)です。

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) T * または T を使用して、パラメーター '% パラメーター %' 一意のポインターへの参照が、決して再割り当てまたはリセット & 代わりにします。 参照してください[C++ コア ガイドライン R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)です。

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、コピー、再割り当て、またはローカルのスマート ポインター '% シンボル %' をリセットします。 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)スマート ポインター パラメーター '% シンボル %' が含まれているポインターへのアクセスにのみ使用されます。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)です。

## <a name="sharedpointer-group"></a>SHARED_POINTER グループ

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)移動、コピー、再割り当て、またはローカルのスマート ポインター '% シンボル %' をリセットします。 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)スマート ポインター パラメーター '% シンボル %' が含まれているポインターへのアクセスにのみ使用されます。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)です。

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)共有ポインター パラメーター '% シンボル %' は右辺値参照によって渡されます。 代わりに値によって渡します。 参照してください[C++ コア ガイドライン R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)です。

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)共有ポインター パラメーター '% シンボル %' が参照渡しであるとはリセットされませんまたは再割り当ています。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)です。

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Shared pointer parameter '%symbol%' is not copied or moved. T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)です。

## <a name="declaration-group"></a>宣言のグループ

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)グローバル初期化子は非 constexpr 関数 '% シンボル %' を呼び出します。 参照してください[C++ コア ガイドライン I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)です。

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)グローバル初期化子 extern オブジェクト '% シンボル %' にアクセスします。 参照してください[C++ コア ガイドライン I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)です。

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)無名のカスタムの構築と破棄を持つオブジェクトを回避します。 参照してください[ES.84: (しようとしないで) 名前のないローカル変数を宣言](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)です。

## <a name="class-group"></a>クラスのグループ

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)を定義する型 '% シンボル %' で、既定の操作を削除するかを定義またはそれらすべてを削除します。 参照してください[C++ コア ガイドライン C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)です。

[C26433 OVERRIDE_EXPLICITLY](c26433.md)関数 '% シンボル %' を 'override' でマークする必要があります。 参照してください[C.128: 仮想関数がただ 1 つの仮想オーバーライドで、または最後に指定する必要があります](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)です。

[C26434 DONT_HIDE_METHODS](C26434.md)関数 '%symbol_1% 'は、非仮想関数 '%symbol_2%' を非表示にします。 参照してください[C++ コア ガイドライン C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)です。

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)関数 '% シンボル %' は 'virtual'、'override' または 'final' の 1 つだけを指定する必要があります。 参照してください[C.128: 仮想関数がただ 1 つの仮想オーバーライドで、または最後に指定する必要があります](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)です。


[C26436 NEED_VIRTUAL_DTOR](C26436.md)型仮想関数で、' % シンボル %'、パブリック仮想、または保護された非仮想デストラクターに必要とします。 参照してください[C++ コア ガイドライン C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)です。


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)オーバーライド デストラクターでは、明示的な 'override' または 'virtual' 指定子は使用しないでください。 参照してください[C.128: 仮想関数がただ 1 つの仮想オーバーライドで、または最後に指定する必要があります](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)です。


## <a name="type-group"></a>種類のグループ

[C26437 DONT_SLICE](C26437.md)スライスはありません。 参照してください[C++ コア ガイドライン ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)です。

## <a name="style-group"></a>スタイル グループ

[C26438 NO_GOTO](C26438.md)回避`goto`です。 参照してください[C++ コア ガイドライン ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)です。

## <a name="function-group"></a>関数のグループ

[C26439 SPECIAL_NOEXCEPT](C26439.md)この種の関数がスローされません。 宣言`noexcept`です。 参照してください[C++ コア ガイドライン F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)です。

[C26440 DECLARE_NOEXCEPT](C26440.md)関数 '% シンボル %' を宣言する`noexcept`です。 参照してください[C++ コア ガイドライン F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)です。

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md)関数が宣言されて**noexcept**が例外をスローする可能性があります関数を呼び出します。
参照してください[C++ コア ガイドライン: F.6: 場合は、関数がスローされませんが、宣言 noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)です。

## <a name="concurrency-group"></a>同時実行のグループ

[C26441 NO_UNNAMED_GUARDS](C26441.md)ガード オブジェクトを指定する必要があります。 参照してください[C++ コア ガイドライン cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)です。

## <a name="const-group"></a>CONST グループ

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md)関数 '% 関数 %' の参照の引数 '% 引数 %' としてマークできる`const`です。 参照してください[C++ コア ガイドライン con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)です。

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): 関数 '% 関数 %' のポインター引数 '% 引数 %' へのポインターとしてマークできる`const`です。 参照してください[C++ コア ガイドライン con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)です。

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) '% 変数 %' を指す値が 1 回しか割り当てられているへのポインターとしてマーク`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) '% 配列 %' の配列の要素が 1 回だけマーク要素で割り当てられた`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) '% 配列 %' の配列の要素を指す値が 1 回だけへのポインターとしてマーク要素で割り当てられた`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。

[C26496 USE_CONST_FOR_VARIABLE](c26496.md)変数 '% 変数 %' が 1 回しか割り当てられている、としてマーク`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md)マークを付けるでしたこの関数 % 関数`constexpr`コンパイル時の評価が必要な場合です。 参照してください[C++ コア ガイドライン F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)です。

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md)この関数の呼び出し関数 % が使用できる`constexpr`コンパイル時の評価が必要な場合です。 参照してください[C++ コア ガイドライン con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)です。

## <a name="type-group"></a>種類のグループ

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md)を使用しない`const_cast`キャストに`const`です。 `const_cast` 不要です。この変換では、constness または揮発性を削除していますされません。 参照してください[C++ コア ガイドライン Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)です。

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md)を使用しない`static_cast`キャストします。 ポリモーフィックな型からキャストには、dynamic_cast を使用する必要があります。 参照してください[C++ コア ガイドライン Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)です。

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) Don't use `reinterpret_cast`. Void * からのキャストが使用できる`static_cast`です。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)を使用しない、`static_cast`の算術変換をします。 かっこ初期化、gsl::narrow_cast、または gsl::narow を使用します。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。

[C26473 NO_IDENTITY_CAST](C26473.md)ソースの種類とターゲットの種類が同じであるポインター型の間でキャストしません。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。

[C26474 NO_IMPLICIT_CAST](C26474.md)変換が暗黙的な可能性がある場合はポインター型の間でキャストしません。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)関数スタイル キャスト C を使用しないでください。 参照してください[C++ コア ガイドライン ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)です。

[C26490 NO_REINTERPRET_CAST](c26490.md)を使用しない`reinterpret_cast`です。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

[C26491 NO_STATIC_DOWNCAST](c26490.md)を使用しない`static_cast`キャストします。 参照してください[C++ コア ガイドライン Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

[C26492 NO_CONST_CAST](c26492.md)を使用しない`const_cast`キャストに`const`です。 参照してください[C++ コア ガイドライン Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

[C26493 NO_CSTYLE_CAST](c26493.md) C スタイルのキャストを使用しません。 参照してください[C++ コア ガイドライン Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

[C26494 VAR_USE_BEFORE_INIT](c26494.md)変数 '% 変数 %' が初期化されていません。 常にオブジェクトを初期化します。 参照してください[C++ コア ガイドライン Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

[C26495 MEMBER_UNINIT](c26495.md)変数 '% 変数 %' が初期化されていません。 常にメンバー変数を初期化します。 参照してください[C++ コア ガイドライン Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。

## <a name="bounds-group"></a>境界グループ

[C26446 USE_GSL_AT](c26446.md)の使用を好む`gsl::at()`未チェックの添字演算子の代わりにします。 参照してください[C++ コア ガイドライン: Bounds.4: 標準ライブラリ関数、および境界のチェックが行われない型を使用しない](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)です。

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
ポインターの算術演算を使用しないでください。 スパンを使用してください。 参照してください[C++ コア ガイドライン Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md)定数式を使用して配列にのみインデックスを作成します。 参照してください[C++ コア ガイドライン Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md)値 % の値が範囲外 (0 の場合、連結 %) の変数 '% 変数 %' です。 配列の境界内にある定数の式を使用して配列へのインデックスのみ。 参照してください[C++ コア ガイドライン Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)式 '%expr% ': ポインター減衰にない配列。 参照してください[C++ コア ガイドライン Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL グループ

[C26445 NO_SPAN_REF](c26445.md)への参照を`gsl::span`または`std::string_view`通知の有効期間に関する問題の可能性があります。
参照してください[C++ コア ガイドライン GSL.view: ビュー](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md)の使用を好む`gsl::at()`未チェックの添字演算子の代わりにします。 参照してください[C++ コア ガイドライン: Bounds.4: 標準ライブラリ関数、および境界のチェックが行われない型を使用しない](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)です。

[C26448 USE_GSL_FINALLY](c26448.md)を使用してください`gsl::finally`最後の操作が対象とした場合。 参照してください[C++ コア ガイドライン: GSL.util: ユーティリティ](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities)です。

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span`または`std::string_view`一時から作成された無効になるときに、一時的なは無効になります。 参照してください[C++ コア ガイドライン: GSL.view: ビュー](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)です。


## <a name="deprecated-warnings"></a>非推奨の警告

次の警告はコア ガイドライン チェッカーの初期の実験用の規則セット内にあるし、は使用されなくなりましたが無視してかまいません。 警告は、上記の一覧からの警告によって置き換えられます。

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>関連項目
[C++ の主要なガイドライン チェッカーを使用します。](using-the-cpp-core-guidelines-checkers.md)
