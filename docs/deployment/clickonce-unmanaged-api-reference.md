---
title: ClickOnce アンマネージ API リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 121b9b3be3c7f942f3ed1d5f7f2600f24d684e2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082140"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce アンマネージ API リファレンス
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dfshim.dll から非管理対象のパブリック Api。  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 消去またはからのすべてのオンライン アプリケーションのアンインストール、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション キャッシュします。  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラーを表す HRESULT を返します。 マネージ例外が発生した場合は、0x80020009 (DISP_E_EXCEPTION) を返します。  
  
### <a name="remarks"></a>Remarks  
 CleanOnlineAppCache の呼び出しが開始されます、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]サービスが実行されていない場合。  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 マニフェストとアクティベーション URL からの展開情報を取得します。  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|型|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|ポインター、`ActivationURL`します。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|ポインター、`PathToDeploymentManifest`します。|LPCWSTR|  
|`pwzApplicationIdentity`|完全なアプリケーション id が返されるを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwIdentityBufferLength`|長さである DWORD へのポインター、 `pwzApplicationIdentity` WCHARs でのバッファー。 これには、NULL 終端文字のための領域が含まれます。|LPDWORD|  
|`pwzProcessorArchitecture`|マニフェストからのアプリケーションの展開のプロセッサ アーキテクチャを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwArchitectureBufferLength`|長さである DWORD へのポインター、 `pwzProcessorArchitecture` WCHARs でのバッファー。|LPDWORD|  
|`pwzApplicationManifestCodebase`|マニフェストから、アプリケーション マニフェストのコードベースを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwCodebaseBufferLength`|長さである DWORD へのポインター、 `pwzApplicationManifestCodebase` WCHARs でのバッファー。|LPDWORD|  
|`pwzDeploymentProvider`|NULL で終わる文字列を受け取るバッファーへのポインターを指定するマニフェストから配置プロバイダー存在する場合。 それ以外の場合、空の文字列が返されます。|LPWSTR|  
|`pdwProviderBufferLength`|長さである DWORD へのポインター、`pwzProviderBufferLength`します。|LPDWORD|  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラーを表す HRESULT を返します。 バッファーが小さすぎる場合は、HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) を返します。  
  
### <a name="remarks"></a>Remarks  
 ポインターを null にするにはできません。 `pcwzActivationUrl` `pcwzPathToDeploymentManifest`空にできません。  
  
 アクティベーション URL をクリーンアップする、呼び出し元の役目です。 必要な場所またはクエリ文字列を削除するが、文字エスケープを追加します。  
  
 入力文字列の長さを制限する、呼び出し元の責任です。 たとえば、URL の最大長は、2 KB です。  
  
## <a name="launchapplication"></a>LaunchApplication  
 起動または配置の URL を使用してアプリケーションをインストールします。  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|型|  
|---------------|-----------------|----------|  
|`deploymentUrl`|配置マニフェストの URL を含む NULL で終わる文字列へのポインター。|LPCWSTR|  
|`data`|将来使用するために予約されています。 NULL にする必要があります。|LPVOID|  
|`flags`|将来使用するために予約されています。 0 を指定する必要があります。|DWORD|  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラーを表す HRESULT を返します。 マネージ例外が発生した場合は、0x80020009 (DISP_E_EXCEPTION) を返します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>