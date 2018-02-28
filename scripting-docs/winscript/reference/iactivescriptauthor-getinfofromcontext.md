---
title: "IActiveScriptAuthor::GetInfoFromContext |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
情報と、指定された文字のアンカー位置は、コードのブロックの型を返します。 IntelliSense、グローバル リスト、およびパラメーターのヒントのメンバーについて情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCode`  
 [in]情報の結果の生成に使用されるコード ブロックの文字列のアドレス。  
  
 `cchCode`  
 [in]コード ブロックの長さ。  
  
 `ichCurrentPosition`  
 [in]ブロックの先頭からの相対文字の位置。  
  
 `dwListTypesRequested`  
 [in]要求されたリストの種類。 次の値の組み合わせが可能です。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|一覧がありません。|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|メンバーの一覧です。|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Enum の一覧です。|  
|SCRIPT_CMPL_PARAMLIST|0x0004|メソッド パラメーター リストを呼び出します。|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|グローバル リストです。|  
  
 SCRIPT_CMPL_GLOBALLIST 型は、既定の入力候補アイテムに他の入力候補の項目を OR 演算子を使用して組み合わせることとして扱われます。 エンジンをまず作成スクリプトは、他の入力候補一覧アイテムの種類の情報を設定しようとします。 失敗した場合、エンジンが SCRIPT_CMPL_GLOBALLIST に追加されます。  
  
 `pdwListTypesProvided`  
 [out]指定されたリストの型。  
  
 `pichListAnchorPosition`  
 [out]現在の位置を格納しているコンテキストの開始インデックス。 開始インデックス ブロックの開始相対パスです。  
  
 これが設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_MEMBERLIST、SCRIPT_CMPL_ENUMLIST、または SCRIPT_CMPL_GLOBALLIST が含まれています。 他の要求されたリストの種類では、結果は定義されません。  
  
 `pichFuncAnchorPosition`  
 [out]現在の位置を含む関数呼び出しの開始インデックス。 開始インデックス ブロックの開始相対パスです。  
  
 現在の位置を格納しているコンテキストが、関数呼び出しである場合にのみ、これは設定されます`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。 それ以外の場合、結果は定義されません。  
  
 `pmemid`  
 [out]内の型によって定義された関数の MEMBERID、 `IProvideMultipleClassInfo``ppunk` out パラメーターです。  
  
 これが設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。  
  
 `piCurrentParameter`  
 [out]現在の位置が格納されているパラメーターのインデックス。 現在の位置がオンの場合、関数名は-1 が返されます。  
  
 `piCurrentParameter`値が設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。  
  
 `ppunk`  
 型については、の形式で提供される、`IProvideMultipleClassInfo`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [IProvideMultipleClassInfo インターフェイス](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)