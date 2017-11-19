---
title: "ClickOnce アンマネージ API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 11e10800ff51abd6f95447d85204a44f8367f551
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce アンマネージ API リファレンス
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]dfshim.dll からアンマネージのパブリック Api です。  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 消去またはからのすべてのオンライン アプリケーションのアンインストール、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション キャッシュします。  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、失敗を表す HRESULT を返します。 マネージ例外が発生した場合は、0x80020009 (DISP_E_EXCEPTION) を返します。  
  
### <a name="remarks"></a>コメント  
 開始 CleanOnlineAppCache を呼び出して、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]サービスが実行されていない場合。  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 マニフェストとアクティベーションの URL からの展開情報を取得します。  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|型|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|ポインター、`ActivationURL`です。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|ポインター、`PathToDeploymentManifest`です。|LPCWSTR|  
|`pwzApplicationIdentity`|完全なアプリケーション id が返されるを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwIdentityBufferLength`|長さを DWORD へのポインター、 `pwzApplicationIdentity` WCHARs 内のバッファー。 これには、NULL 終端文字のスペースが含まれます。|LPDWORD|  
|`pwzProcessorArchitecture`|マニフェストからのアプリケーションの配置のプロセッサ アーキテクチャを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwArchitectureBufferLength`|長さを DWORD へのポインター、 `pwzProcessorArchitecture` WCHARs 内のバッファー。|LPDWORD|  
|`pwzApplicationManifestCodebase`|マニフェストからのアプリケーション マニフェストのコードベースを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwCodebaseBufferLength`|長さを DWORD へのポインター、 `pwzApplicationManifestCodebase` WCHARs 内のバッファー。|LPDWORD|  
|`pwzDeploymentProvider`|NULL で終わる文字列を受け取るバッファーへのポインターを指定するマニフェストから配置プロバイダ存在する場合。 それ以外の場合、空の文字列が返されます。|LPWSTR|  
|`pdwProviderBufferLength`|長さを DWORD へのポインター、`pwzProviderBufferLength`です。|LPDWORD|  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、失敗を表す HRESULT を返します。 バッファーが小さすぎる場合は、HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) を返します。  
  
### <a name="remarks"></a>コメント  
 ポインターを null にするにはできません。 `pcwzActivationUrl`および`pcwzPathToDeploymentManifest`空にしないでください。  
  
 呼び出し元のライセンス認証の URL をクリーンアップします。 たとえば、エスケープを追加する文字が必要な場所またはクエリ文字列を削除します。  
  
 入力文字列の長さを制限する、呼び出し元の役割です。 たとえば、URL の最大長は 2 KB です。  
  
## <a name="launchapplication"></a>LaunchApplication  
 起動するか、デプロイメント URL を使用して、アプリケーションをインストールします。  
  
### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|型|  
|---------------|-----------------|----------|  
|`deploymentUrl`|配置マニフェストの URL を表す NULL で終わる文字列へのポインター。|LPCWSTR|  
|`data`|将来使用するために予約されています。 NULL にする必要があります。|LPVOID|  
|`flags`|将来使用するために予約されています。 0 にする必要があります。|DWORD|  
  
### <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、失敗を表す HRESULT を返します。 マネージ例外が発生した場合は、0x80020009 (DISP_E_EXCEPTION) を返します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>