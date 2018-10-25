---
title: SccGetExtendedCapabilities 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2336a14c6d0030c0243ab7de0f5694dc159ed84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926307"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [in]テスト対象の機能が拡張を指定するフラグ (拡張機能コード表を参照して[機能フラグ](../extensibility/capability-flags.md)の考えられるフラグ)。  
  
 pbSupported  
 [out]0 以外を返します (`TRUE`) 場合は、指定された機能がサポートされています。 それ以外の場合、0 を返します (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|正常に完了した取得機能の操作です。|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|不明または未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 オンデマンド; でこのメソッドが呼び出されますつまり、機能の 1 つは、テストする必要がある、このメソッドが呼び出されますかを判断する機能がサポートされています。 一度に 1 つのみのフラグが指定されます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [エラー コード](../extensibility/error-codes.md)   
 [機能フラグ](../extensibility/capability-flags.md)

