---
title: "SymTagEnum |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ffafd105a6e492f4ce1dc1837137c6020be7dc2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="symtagenum"></a>SymTagEnum
記号の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elements  
 `SymTagNull`  
 シンボルに型が含まれていないことを示します。  
  
 `SymTagExe`  
 シンボルが .exe ファイルであることを示します。 1 つだけを使用する必要がある`SymTagExe`シンボル ストアごとのシンボルです。 これにより、グローバル スコープとして機能しは構文上の親がありません。  
  
 `SymTagCompiland`  
 コンパイル単位シンボルをシンボル ストアの各コンポーネントのコンパイル単位を示します。 ネイティブ アプリケーションは、`SymTagCompiland`シンボルが、イメージにリンクされたオブジェクト ファイルに対応します。 Microsoft Intermediate Language (MSIL) のイメージの一部の種類の場合は、クラスごとの 1 つのコンパイル単位です。  
  
 `SymTagCompilandDetails`  
 シンボルが、コンパイル単位の拡張属性が含まれていることを示します。 これらのプロパティを取得するには、コンパイル単位シンボルを読み込む必要があります。  
  
 `SymTagCompilandEnv`  
 シンボルが、コンパイル単位に対して定義されている環境文字列であることを示します。  
  
 `SymTagFunction`  
 シンボルが関数であることを示します。  
  
 `SymTagBlock`  
 シンボルが入れ子になったブロックであることを示します。  
  
 `SymTagData`  
 シンボルがデータであることを示します。  
  
 `SymTagAnnotation`  
 コードの注釈のシンボルであることを示します。 このシンボルの子が定数のデータの文字列 (`SymTagData`、 `LocIsConstant`、 `DataIsConstant`)。 ほとんどのクライアントは、このシンボルを無視します。  
  
 `SymTagLabel`  
 シンボルはラベルであることを示します。  
  
 `SymTagPublicSymbol`  
 シンボルは、パブリック シンボルであることを示します。 ネイティブ アプリケーションは、このシンボルは、イメージをリンクする際に発生した COFF 外部シンボルです。  
  
 `SymTagUDT`  
 シンボルが、ユーザー定義型 (構造体、クラス、または和集合) であることを示します。  
  
 `SymTagEnum`  
 シンボルが列挙型であることを示します。  
  
 `SymTagFunctionType`  
 シンボルが関数のシグネチャの型であることを示します。  
  
 `SymTagPointerType`  
 シンボルがポインター型であることを示します。  
  
 `SymTagArrayType`  
 シンボルが配列型であることを示します。  
  
 `SymTagBaseType`  
 シンボルが基本型であることを示します。  
  
 `SymTagTypedef`  
 シンボルがあることを示します、 `typedef`、つまり、別の型のエイリアスです。  
  
 `SymTagBaseClass`  
 シンボルがユーザー定義型の基底クラスであることを示します。  
  
 `SymTagFriend`  
 シンボルがユーザー定義型のフレンドであることを示します。  
  
 `SymTagFunctionArgType`  
 シンボルが関数の引数であることを示します。  
  
 `SymTagFuncDebugStart`  
 シンボルが関数のプロローグ コードの終了位置であることを示します。  
  
 `SymTagFuncDebugEnd`  
 シンボルが関数のエピローグ コードの開始位置であることを示します。  
  
 `SymTagUsingNamespace`  
 シンボルが、現在のスコープでアクティブな名前空間の名前であることを示します。  
  
 `SymTagVTableShape`  
 シンボルが仮想テーブルの説明であることを示します。  
  
 `SymTagVTable`  
 シンボルが仮想テーブルへのポインターであることを示します。  
  
 `SymTagCustom`  
 シンボルがカスタム シンボルであり、DIA. で解釈されないことを示します  
  
 `SymTagThunk`  
 シンボルがサンクを 16、32 ビット コードの間でデータを共有するために使用されることを示します。  
  
 `SymTagCustomType`  
 シンボルがカスタム コンパイラ シンボルであることを示します。  
  
 `SymTagManagedType`  
 シンボルがメタデータであることを示します。  
  
 `SymTagDimension`  
 シンボルが、FORTRAN 多次元配列であることを示します。  
  
 `SymTagCallSite`  
 シンボルが呼び出しサイトを表すことを示します。  
  
 `SymTagInlineSite`  
 シンボルがインライン サイトを表すことを示します。  
  
 `SymTagBaseInterface`  
 シンボルは、基本インターフェイスであることを示します。  
  
 `SymTagVectorType`  
 シンボルがベクトルの型であることを示します。  
  
 `SymTagMatrixType`  
 シンボルがマトリックス型であることを示します。  
  
 `SymTagHLSLType`  
 シンボルが高レベルのシェーダー言語の型であることを示します。  
  
## <a name="remarks"></a>コメント  
 デバッグ ファイル内のすべてのシンボルでは、シンボルの型を指定する識別タグがあります。  
  
 この列挙体の値がへの呼び出しによって返される、 [idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)メソッドです。  
  
 この列挙体の値は、特定の記号の型への検索のスコープを制限する次のメソッドに渡されます。  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Idiasession::findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Idiasession::findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Idiasession::findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Idiasession::findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Idiasession::findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Idiasession::findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)