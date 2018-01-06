---
title: "Visual Studio の C++ の主要なガイドライン チェッカー リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c17574722804409b58d648af66b255888e945db2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="c-core-guidelines-checker-reference"></a>C++ の主要なガイドライン チェッカー参照
このセクションでは、C++ の主要なガイドラインのチェックの警告を一覧表示します。 コード分析の詳細については、次を参照してください。 [/analyze (コード分析)](/cpp/build/reference/analyze-code-analysis)と[クイック スタート: c/c++ コード分析](../code-quality/quick-start-code-analysis-for-c-cpp.md)です。  
  
**注**: いくつかの警告が 2 つ以上のグループに所属していないすべての警告リファレンス トピックです。

## <a name="ownerpointer-group"></a>OWNER_POINTER グループ

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  
  移動コンス トラクターがある場合は、ヒープに割り当てられたのではなくスコープを持つオブジェクトを返します。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。 
     
[C26403 RESET_OR_DELETE_OWNER](C26403.md)  
  リセットするか、または所有者を明示的に削除する\<T > ポインターが '% 変数 %' です。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。  
     
[C26404 DONT_DELETE_INVALID](C26404.md)  
  所有者を削除しないでください\<T > 無効な状態になる可能性があります。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。  

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)  
  所有者に割り当てないでください\<T > 有効な状態である可能性があります。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。  

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)  
  所有者に生のポインターを割り当てないでください\<T > です。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。  
  
[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)  
  スコープを持つオブジェクトを必要に応じて、ヒープには割り当てませんが不必要にします。 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。  

[C26429 USE_NOTNULL](C26429.md)  
  '% シンボル %' のシンボルがないことをテストされていません、not_ としてマークできます。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  

[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  '% シンボル %' のシンボルは、すべてのパスでないことをテストされていません。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  式 '%expr% ' の型は、既に、gsl::not_null です。 ないことをテストしないでください。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  

## <a name="rawpointer-group"></a>RAW_POINTER グループ
 
[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)  
所有者を割り当て、または関数の呼び出しの結果を割り当てないでください\<T > への生のポインター値を返す、所有者を使用して<T>代わりにします。 参照してください[C++ コア ガイドライン I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)です。 

[C26401 DONT_DELETE_NON_OWNER](c26401.md)  
所有者ではなく生のポインターを削除しないでください\<T > です。 参照してください[C++ コア ガイドライン I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)です。 

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  移動コンス トラクターがある場合は、ヒープに割り当てられたのではなくスコープを持つオブジェクトを返します。 参照してください[C++ コア ガイドライン R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)です。 
 
[C26408 NO_MALLOC_FREE](C26408.md)  
  Delete で新規の nothrow バージョンを必要に応じてに malloc() および free() をしないでください。 参照してください[C++ コア ガイドライン R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)です。  
  
[C26409 NO_NEW_DELETE](C26409.md)  
  新しい呼び出しを避けるため、明示的に削除して、std::make_unique を使用して\<T > 代わりにします。 参照してください[C++ コア ガイドライン R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)です。  

[C26429 USE_NOTNULL](C26429.md)  
  '% シンボル %' のシンボルがないことをテストされていません、not_ としてマークできます。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  
  
[C26430 TEST_ON_ALL_PATHS](C26430.md)  
  '% シンボル %' のシンボルは、すべてのパスでないことをテストされていません。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  
  
[C26431 DONT_TEST_NOTNULL](C26431.md)  
  式 '%expr% ' の型は、既に、gsl::not_null です。 ないことをテストしないでください。 参照してください[C++ コア ガイドライン F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)です。  
  
[C26481 NO_POINTER_ARITHMETIC](C26481.md)  
  ポインターの算術演算を使用しないでください。 スパンを使用してください。 参照してください[C++ コア ガイドライン Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  式 '%expr% ': ポインター減衰にない配列。 参照してください[C++ コア ガイドライン Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  

## <a name="uniquepointer-group"></a>UNIQUE_POINTER グループ
  
[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)  
  パラメーター '% パラメーター %' への参照は、`const`一意のポインター、const T * または const T を使用して & 代わりにします。 参照してください[C++ コア ガイドライン R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)です。  
     
[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)  
  T * または T を使用して、パラメーター '% パラメーター %' 一意のポインターへの参照が、決して再割り当てまたはリセット & 代わりにします。 参照してください[C++ コア ガイドライン R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)です。  
     
[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  移動、コピー、再割り当てまたはローカルのスマート ポインター '% シンボル %' をリセットします。 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  スマート ポインター パラメーター '% シンボル %' は、アクセスが含まれているポインターにのみ使用されます。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)です。  

## <a name="sharedpointer-group"></a>SHARED_POINTER グループ

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)  
  移動、コピー、再割り当てまたはローカルのスマート ポインター '% シンボル %' をリセットします。 参照してください[C++ コア ガイドライン R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)です。  
    
[C26415 SMART_PTR_NOT_NEEDED](C26415.md)  
  スマート ポインター パラメーター '% シンボル %' は、アクセスが含まれているポインターにのみ使用されます。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)です。  
    
[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)  
  共有ポインター パラメーター '% シンボル %' は、右辺値参照で渡されます。 代わりに値によって渡します。 参照してください[C++ コア ガイドライン R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)です。  
  
[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)  
  共有ポインター パラメーター '% シンボル %' が参照渡しであるとはリセットされませんまたは再割り当ています。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)です。  
  
[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)  
  共有ポインター パラメーター '% シンボル %' のコピーまたは移動されていません。 T * または T を使用すると、代わりにします。 参照してください[C++ コア ガイドライン R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)です。  

## <a name="declaration-group"></a>宣言のグループ
    
[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)  
  グローバル初期化子は非 constexpr 関数 '% シンボル %' を呼び出します。 参照してください[C++ コア ガイドライン I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)です。  
  
[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)  
  グローバル初期化子では、extern オブジェクト '% シンボル %' にアクセスします。 参照してください[C++ コア ガイドライン I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)です。  
  
## <a name="class-group"></a>クラスのグループ
    
[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)  
  定義または型 '% シンボル %' で、既定の操作を削除する場合は、定義またはそれらすべてを削除します。 参照してください[C++ コア ガイドライン C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)です。  
  
[C26434 DONT_HIDE_METHODS](C26434.md)  
  関数 '%symbol_1% 'には、非仮想関数 '%symbol_2%' が非表示にします。 参照してください[C++ コア ガイドライン C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)です。  
  
[C26436 NEED_VIRTUAL_DTOR](C26436.md)  
  'シンボル %' 仮想関数を持つ型には、どちらかパブリック仮想、または保護された非仮想デストラクターが必要があります。 参照してください[C++ コア ガイドライン C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)です。  

## <a name="type-group"></a>種類のグループ
    
[C26437 DONT_SLICE](C26437.md)  
  スライスはありません。 参照してください[C++ コア ガイドライン ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)です。  

## <a name="style-group"></a>スタイル グループ  
[C26438 NO_GOTO](C26438.md)  
  回避`goto`です。 参照してください[C++ コア ガイドライン ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)です。  
  
## <a name="function-group"></a>関数のグループ
    
[C26439 SPECIAL_NOEXCEPT](C26439.md)  
  この種の関数がスローされません。 宣言`noexcept`です。 参照してください[C++ コア ガイドライン F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)です。  
  
[C26440 DECLARE_NOEXCEPT](C26440.md)  
  関数 '% シンボル %' を宣言する`noexcept`です。 参照してください[C++ コア ガイドライン F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)です。  

## <a name="concurrency-group"></a>同時実行のグループ
    
[C26441 NO_UNNAMED_GUARDS](C26441.md)  
 ガード オブジェクトを指定する必要があります。 参照してください[C++ コア ガイドライン cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)です。  

## <a name="const-group"></a>CONST グループ
    
C26460 USE_CONST_REFERENCE_ARGUMENTS:  
  関数 '% 関数 %' の参照の引数 '% 引数 %' としてマークできる`const`です。 参照してください[C++ コア ガイドライン con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)です。  
  
C26461 USE_CONST_POINTER_ARGUMENTS: 関数 '% 関数 %' のポインター引数 '% 引数 %' へのポインターとしてマークできる`const`です。 参照してください[C++ コア ガイドライン con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)です。  
  
C26462 USE_CONST_POINTER_FOR_VARIABLE:  
  '% 変数 %' を指す値が 1 回しか割り当てられているへのポインターとしてマーク`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。  
  
C26463 USE_CONST_FOR_ELEMENTS:  
  '% 配列 %' の配列の要素が 1 回だけマーク要素で割り当てられた`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。  
  
C26464 USE_CONST_POINTER_FOR_ELEMENTS:  
  '% 配列 %' の配列の要素を指す値が 1 回だけへのポインターとしてマーク要素で割り当てられた`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。  

C26496 USE_CONST_FOR_VARIABLE:  
  変数 '% 変数 %' が 1 回しか割り当てられている、としてマーク`const`です。 参照してください[C++ コア ガイドライン con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)です。  
  
C26497 USE_CONSTEXPR_FOR_FUNCTION:  
  この関数 % 関数をマークでした`constexpr`コンパイル時の評価が必要な場合です。 参照してください[C++ コア ガイドライン F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)です。  
  
C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL:  
  この関数の呼び出し関数 % が使用できる`constexpr`コンパイル時の評価が必要な場合です。 参照してください[C++ コア ガイドライン con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)です。  

## <a name="type-group"></a>種類のグループ
C26465 NO_CONST_CAST_UNNECESSARY:  
  使用しない`const_cast`キャストに`const`です。 `const_cast`不要です。この変換では、constness または揮発性を削除していますされません。 参照してください[C++ コア ガイドライン Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)です。  
  
C26466 NO_STATIC_DOWNCAST_POLYMORPHIC:  
  使用しない`static_cast`キャストします。 ポリモーフィックな型からキャストには、dynamic_cast を使用する必要があります。 参照してください[C++ コア ガイドライン Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)です。  
  
C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR:  
  使用しない`reinterpret_cast`です。 Void * からのキャストが使用できる`static_cast`です。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。  
  
[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)  
  使用しない、`static_cast`の算術変換をします。 かっこ初期化、gsl::narrow_cast または gsl::narow を使用します。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。  
  
[C26473 NO_IDENTITY_CAST](C26473.md)  
  ソースの種類とターゲットの種類が同じであるポインター型の間でキャストしません。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。  
  
[C26474 NO_IMPLICIT_CAST](C26474.md)  
  変換が暗黙的な可能性がある場合はポインター型の間でキャストしません。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)です。  
  
[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)  
  関数スタイル キャスト C を使用しないでください。 参照してください[C++ コア ガイドライン ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)です。  
     
C26490 NO_REINTERPRET_CAST:  
  使用しない`reinterpret_cast`です。 参照してください[C++ コア ガイドライン Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。  
  
C26491 NO_STATIC_DOWNCAST:  
  使用しない`static_cast`キャストします。 参照してください[C++ コア ガイドライン Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。  
  
C26492 NO_CONST_CAST:  
  使用しない`const_cast`キャストに`const`です。 参照してください[C++ コア ガイドライン Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。  
    
C26493 NO_CSTYLE_CAST:  
  C スタイルのキャストを使用しないでください。 参照してください[C++ コア ガイドライン Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。 
     
C26494 VAR_USE_BEFORE_INIT:  
  '% 変数 %' の変数は初期化されていません。 常にオブジェクトを初期化します。 参照してください[C++ コア ガイドライン Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。  
  
C26495 MEMBER_UNINIT:  
  '% 変数 %' の変数は初期化されていません。 常にメンバー変数を初期化します。 参照してください[C++ コア ガイドライン Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)です。  
  
## <a name="bounds-group"></a>境界グループ

[C26481 NO_POINTER_ARITHMETIC](C26481.md)   
  ポインターの算術演算を使用しないでください。 スパンを使用してください。 参照してください[C++ コア ガイドライン Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  
  
C26482 NO_DYNAMIC_ARRAY_INDEXING:  
  定数式を使用して配列へのインデックスのみ。 参照してください[C++ コア ガイドライン Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  
  
C26483 STATIC_INDEX_OUT_OF_RANGE:  
  % 値の値が範囲外 (0 の場合、連結 %) の変数 '% 変数 %' です。 配列の境界内にある定数の式を使用して配列へのインデックスのみ。 参照してください[C++ コア ガイドライン Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)   
  式 '%expr% ': ポインター減衰にない配列。 参照してください[C++ コア ガイドライン Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)です。  
  
## <a name="see-also"></a>参照  
[C++ の主要なガイドライン チェッカーを使用します。](using-the-cpp-core-guidelines-checkers.md)
