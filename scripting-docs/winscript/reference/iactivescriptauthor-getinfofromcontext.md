---
title: IActiveScriptAuthor::GetInfoFromContext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d32e2864f42fa9a2bfc30cfe83da7d4e021dfd0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088869"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
返しますでは、コードのブロックの情報と、指定された文字のアンカー位置を入力します。 これにより、IntelliSense、グローバル リスト、およびパラメーターのヒント、メンバーの情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]文字は、ブロックの先頭からの相対の位置します。  
  
 `dwListTypesRequested`  
 [in]要求されたリストの型。 次の値の組み合わせになります。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|一覧がありません。|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|メンバーの一覧。|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Enum の一覧。|  
|SCRIPT_CMPL_PARAMLIST|0x0004|パラメーター リストのメソッドを呼び出します。|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|グローバル リスト。|  
  
 SCRIPT_CMPL_GLOBALLIST 型は、組み合わせることができるその他の入力候補の項目を OR 演算子を使用して既定の入力候補アイテムとして扱われます。 エンジンをまず作成スクリプトは、その他のコンプリート リスト項目の種類の情報を入力しようとします。 失敗した場合は、エンジンが SCRIPT_CMPL_GLOBALLIST 設定されます。  
  
 `pdwListTypesProvided`  
 [out]表示された一覧の型。  
  
 `pichListAnchorPosition`  
 [out]現在の位置を格納しているコンテキストの開始インデックス。 開始インデックスは、ブロックの先頭からの相対です。  
  
 これは設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_MEMBERLIST、SCRIPT_CMPL_ENUMLIST、または SCRIPT_CMPL_GLOBALLIST が含まれています。 その他の要求されたリストの場合、結果は定義されません。  
  
 `pichFuncAnchorPosition`  
 [out]現在の位置を含む関数呼び出しの開始インデックス。 開始インデックスは、ブロックの先頭からの相対です。  
  
 現在の位置を格納しているコンテキストが、関数呼び出しである場合にのみ、これは設定されます`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。 それ以外の場合、結果は定義されません。  
  
 `pmemid`  
 [out]内の型で定義されている関数の MEMBERID、 `IProvideMultipleClassInfo``ppunk` out パラメーター。  
  
 これは設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。  
  
 `piCurrentParameter`  
 [out]現在の位置を含むパラメーターのインデックス。 関数名が現在の位置にある場合は、-1 が返されます。  
  
 `piCurrentParameter`値が設定される場合にのみ`dwListTypesRequested`SCRIPT_CMPL_PARAMLIST が含まれています。  
  
 `ppunk`  
 形式で提供される型情報、`IProvideMultipleClassInfo`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IProvideMultipleClassInfo インターフェイス](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)