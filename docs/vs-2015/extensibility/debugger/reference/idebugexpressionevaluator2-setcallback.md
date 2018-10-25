---
title: IDebugExpressionEvaluator2::SetCallback |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe32019bf5ec90dd428cada91a00865b4edefd72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890427"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

メトリックの設定を読み取るデバッガー エンジン (DE) を使用するコールバック インターフェイスを指定するには、式エバリュエーター (EE) を有効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in]設定のコールバックを使用するインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、式エバリュエーターは、メトリックの設定の読み取りに使用できるセッション デバッグ マネージャーのインターフェイスを提供します。 メトリックを読み取ります。 へのリモート デバッグで役に立ちますが、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]コンピューター。  
  
## <a name="example"></a>例  
 次の例のこのメソッドを実装する方法を示しています、 **CEE**を公開するオブジェクト、 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)インターフェイス。  
  
```cpp#  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

