---
title: SymTagEnum |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a74e47158345bf271482c58c2aa44957cb7e3a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937292"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

記号の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 シンボルに型がないことを示します。  
  
 `SymTagExe`  
 シンボルが .exe ファイルであることを示します。 1 つしかない`SymTagExe`シンボル ストアごとのシンボルです。 グローバル スコープとして機能し、構文上の親はありません。  
  
 `SymTagCompiland`  
 コンパイル単位シンボルをシンボル ストアの場合は、各コンパイル単位コンポーネントを示します。 ネイティブ アプリケーションは、`SymTagCompiland`シンボルがイメージにリンクされているオブジェクト ファイルに対応しています。 Microsoft Intermediate Language (MSIL) のイメージの一部の種類の場合は、クラスごとの 1 つのコンパイル単位です。  
  
 `SymTagCompilandDetails`  
 シンボルが、コンパイル単位の拡張属性が含まれていることを示します。 これらのプロパティを取得するには、コンパイル単位シンボルを読み込む必要があります。  
  
 `SymTagCompilandEnv`  
 シンボルが定義されている、コンパイル単位の環境文字列であることを示します。  
  
 `SymTagFunction`  
 シンボルが関数であることを示します。  
  
 `SymTagBlock`  
 シンボルが入れ子になったブロックであることを示します。  
  
 `SymTagData`  
 シンボルがデータであることを示します。  
  
 `SymTagAnnotation`  
 コードの注釈のシンボルであることを示します。 このシンボルの子は定数データの文字列 (`SymTagData`、 `LocIsConstant`、 `DataIsConstant`)。 ほとんどのクライアントは、このシンボルを無視します。  
  
 `SymTagLabel`  
 シンボルはラベルであることを示します。  
  
 `SymTagPublicSymbol`  
 シンボルは、パブリック シンボルであることを示します。 ネイティブ アプリケーションは、このシンボルは、イメージをリンク中に発生した COFF 外部シンボルです。  
  
 `SymTagUDT`  
 シンボルは、ユーザー定義型 (構造体、クラス、または和集合) であることを示します。  
  
 `SymTagEnum`  
 シンボルが列挙体であることを示します。  
  
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
 シンボルは、ユーザー定義型の基底クラスであることを示します。  
  
 `SymTagFriend`  
 シンボルは、ユーザー定義型のフレンドであることを示します。  
  
 `SymTagFunctionArgType`  
 シンボルが関数の引数であることを示します。  
  
 `SymTagFuncDebugStart`  
 シンボルは、関数のプロローグ コードの終了位置であることを示します。  
  
 `SymTagFuncDebugEnd`  
 シンボルは、関数のエピローグ コードの開始位置であることを示します。  
  
 `SymTagUsingNamespace`  
 シンボルが、現在のスコープでアクティブな名前空間の名前であることを示します。  
  
 `SymTagVTableShape`  
 シンボルは、仮想テーブルの説明であることを示します。  
  
 `SymTagVTable`  
 シンボルは、仮想テーブルのポインターであることを示します。  
  
 `SymTagCustom`  
 シンボルがカスタム シンボルであり、中で解釈されないことを示します  
  
 `SymTagThunk`  
 シンボルがサンク 16、32 ビット コードの間でデータを共有するために使用されることを示します。  
  
 `SymTagCustomType`  
 シンボルは、カスタム コンパイラ シンボルであることを示します。  
  
 `SymTagManagedType`  
 メタデータのシンボルがあることを示します。  
  
 `SymTagDimension`  
 シンボルは、FORTRAN の多次元配列であることを示します。  
  
 `SymTagCallSite`  
 シンボルが呼び出しサイトを表すことを示します。  
  
 `SymTagInlineSite`  
 シンボルがインライン サイトを表すことを示します。  
  
 `SymTagBaseInterface`  
 シンボルは、基本インターフェイスであることを示します。  
  
 `SymTagVectorType`  
 シンボルは、ベクター型であることを示します。  
  
 `SymTagMatrixType`  
 シンボルがマトリックス型であることを示します。  
  
 `SymTagHLSLType`  
 シンボルが High Level Shader Language 型であることを示します。  
  
## <a name="remarks"></a>Remarks  
 デバッグ ファイル内のすべてのシンボルはシンボルの種類を指定する識別タグがあります。  
  
 この列挙体の値が呼び出しによって返される、 [idiasymbol::get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)メソッド。  
  
 この列挙体の値は、特定の記号の型を検索のスコープを制限する次のメソッドに渡されます。  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>必要条件  
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



