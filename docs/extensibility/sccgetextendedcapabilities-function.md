---
title: "SccGetExtendedCapabilities 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetExtendedCapabilities
helpviewer_keywords: SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5134116a9d6a8d7872692e88ecd8adf60e9c02e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 関数
この関数は、ソース管理プラグインでサポートされているその他の機能を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 lSccExCaps  
 [in]テスト対象の機能が拡張を指定するフラグ (拡張機能コード表を参照して[機能フラグ](../extensibility/capability-flags.md)の考えられるフラグ)。  
  
 pbSupported  
 [out]0 以外を返します (`TRUE`)、指定された機能がサポートされる場合は、0 を返しますそれ以外の場合 (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|Get 機能操作が完了しました。|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|不明または未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドはオンデマンドです。つまり、機能をテストする必要があります、このメソッドが呼び出されますかどうかを機能がサポートされています。 一度に 1 つだけのフラグが指定されています。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [エラー コード](../extensibility/error-codes.md)   
 [機能フラグ](../extensibility/capability-flags.md)