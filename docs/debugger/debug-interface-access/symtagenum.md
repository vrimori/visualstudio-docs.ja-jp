---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum 列挙型"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルの種類を指定します。  
  
## 構文  
  
```cpp#  
enum SymTagEnum {   
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
  
## Elements  
 `SymTagNull`  
 シンボルが種類を持っていないことを示します。  
  
 `SymTagExe`  
 .Exe ファイルのシンボルであることを示します。  1 つしかない`SymTagExe`シンボルをシンボル ストアごと。  グローバル スコープとして機能し、構文の親はありません。  
  
 `SymTagCompiland`  
 各コンパイル コンポーネントのシンボル ストアのコンパイル シンボルを指定します。  ネイティブ アプリケーション用`SymTagCompiland`記号を対応するイメージにリンクされたオブジェクトファイルにします。  Microsoft 中間言語 \(MSIL\) のイメージの種類によっては、各クラスの 1 つのコンパイルがありません。  
  
 `SymTagCompilandDetails`  
 シンボルにするコンパイル単位内の拡張属性が含まれていることを示します。  これらのプロパティを取得するコンパイル シンボルをロードする必要があります。  
  
 `SymTagCompilandEnv`  
 コンパイル単位内で定義された環境文字列のシンボルであることを示します。  
  
 `SymTagFunction`  
 シンボル関数であることを示します。  
  
 `SymTagBlock`  
 入れ子になったブロックのシンボルであることを示します。  
  
 `SymTagData`  
 データのシンボルであることを示します。  
  
 `SymTagAnnotation`  
 シンボルはコードのコメントをであることを示します。  この記号の子は、定数のデータ文字列 \(`SymTagData`、 `LocIsConstant`、 `DataIsConstant`\)。  ほとんどのクライアントは、この記号を無視します。  
  
 `SymTagLabel`  
 シンボルはラベルであることを示します。  
  
 `SymTagPublicSymbol`  
 パブリック シンボルのシンボルであることを示します。  ネイティブ アプリケーションでは、このシンボルは、イメージをリンクする際に発生した、COFF 外部記号です。  
  
 `SymTagUDT`  
 シンボルがユーザー定義型 \(構造体、クラス、または共用体\) であることを示します。  
  
 `SymTagEnum`  
 列挙型のシンボルであることを示します。  
  
 `SymTagFunctionType`  
 シンボル関数シグネチャの一種であることを示します。  
  
 `SymTagPointerType`  
 シンボルがポインター型であることを示します。  
  
 `SymTagArrayType`  
 配列型のシンボルであることを示します。  
  
 `SymTagBaseType`  
 基本型のシンボルであることを示します。  
  
 `SymTagTypedef`  
 シンボルであることを示す、 `typedef`、つまり、別の種類の別名。  
  
 `SymTagBaseClass`  
 シンボルがユーザー定義型の基本クラスであることを示します。  
  
 `SymTagFriend`  
 シンボルがユーザー定義型のフレンドであることを示します。  
  
 `SymTagFunctionArgType`  
 シンボルは、関数の引数であることを示します。  
  
 `SymTagFuncDebugStart`  
 記号が、関数のプロローグ コードの終了位置であることを示します。  
  
 `SymTagFuncDebugEnd`  
 シンボル関数のエピローグ コードの開始位置であることを示します。  
  
 `SymTagUsingNamespace`  
 名前空間名、現在のスコープで有効なシンボルであることを示します。  
  
 `SymTagVTableShape`  
 仮想テーブルの説明のシンボルであることを示します。  
  
 `SymTagVTable`  
 シンボルは、仮想テーブル ポインターことを示します。  
  
 `SymTagCustom`  
 シンボルは、カスタムのシンボルであり、中で解釈されないことを示しています。  
  
 `SymTagThunk`  
 シンボル、サンクの 16 と 32 ビット コード間でデータを共有するために使用されることを示します。  
  
 `SymTagCustomType`  
 カスタム コンパイラのシンボルのシンボルであることを示します。  
  
 `SymTagManagedType`  
 メタデータ内のシンボルであることを示します。  
  
 `SymTagDimension`  
 シンボルは、FORTRAN の多次元配列であることを示します。  
  
 `SymTagCallSite`  
 シンボルの呼び出しサイトを表すことを示します。  
  
 `SymTagInlineSite`  
 シンボルが、インラインのサイトを表すことを示します。  
  
 `SymTagBaseInterface`  
 シンボルは、基本インターフェイスであることを示します。  
  
 `SymTagVectorType`  
 シンボルは、ベクター型であることを示します。  
  
 `SymTagMatrixType`  
 シンボルは、\[マトリックス\] 種類であることを示します。  
  
 `SymTagHLSLType`  
 シンボルは、高レベル シェーダー言語の一種であることを示します。  
  
## 解説  
 デバッグ ファイル内のすべてのシンボルは、シンボルのタイプを指定しますを識別するタグがあります。  
  
 この列挙体の値への呼び出しによって返される、 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)メソッド。  
  
 この列挙体の値を検索するには、シンボルの特定の種類の範囲を制限するには、次の方法で渡されます。  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## 必要条件  
 ヘッダー: cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)