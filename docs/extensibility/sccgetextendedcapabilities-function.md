---
title: "SccGetExtendedCapabilities 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0331979eaae065730dab5d5daf0e226844d5e7a
ms.lasthandoff: 02/22/2017

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
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 lSccExCaps  
 [in]テスト対象の機能が拡張を指定するフラグ (拡張機能コード表を参照して[機能フラグ](../extensibility/capability-flags.md)可能なフラグの)。  
  
 pbSupported  
 [out]0 以外を返します (`TRUE`)、指定された機能がサポートされています。 それ以外の場合、0 が返されます (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|Get 機能操作が完了しました。|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|不明または未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは (オンデマンド)。つまり、機能の&1; つは、テストする必要がある、このメソッドが呼び出されますかどうかを機能がサポートされています。 一度に&1; つだけのフラグが指定されています。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [エラー コード](../extensibility/error-codes.md)   
 [機能フラグ](../extensibility/capability-flags.md)
