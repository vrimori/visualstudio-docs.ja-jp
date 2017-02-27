---
title: "ClickOnce アンマネージ API リファレンス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CleanOnlineAppCache [ClickOnce アンマネージ]"
  - "CleanOnlineAppCacheW インターフェイス [ClickOnce アンマネージ]"
  - "ClickOnce, アンマネージ API"
  - "GetDeploymentDataFromManifest [ClickOnce アンマネージ]"
  - "LaunchApplication [ClickOnce アンマネージ]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 6
---
# ClickOnce アンマネージ API リファレンス
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

dfshim.dll の [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アンマネージ パブリック API です。  
  
## CleanOnlineAppCache  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーション キャッシュから、すべてのオンライン アプリケーションを消去またはアンインストールします。  
  
### 戻り値  
 処理が正常に終了した場合は、S\_OK を返します。それ以外の場合は、エラーを表す HRESULT を返します。  マネージ例外が発生すると、0x80020009 \(DISP\_E\_EXCEPTION\) を返します。  
  
### 解説  
 CleanOnlineAppCache を呼び出すと、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] サービスが開始されます \(まだ実行されていない場合\)。  
  
## GetDeploymentDataFromManifest  
 マニフェストとアクティベーション URL から配置情報を取得します。  
  
### パラメーター  
  
|パラメーター|Description|種類|  
|------------|-----------------|--------|  
|`pcwzActivationUrl`|`ActivationURL` へのポインター。|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest` へのポインター。|LPCWSTR|  
|`pwzApplicationIdentity`|NULL で終わる文字列を受け取るバッファーへのポインター。文字列には、返される完全なアプリケーション ID が指定されます。|LPWSTR|  
|`pdwIdentityBufferLength`|`pwzApplicationIdentity` バッファーの長さを示す DWORD へのポインター \(WCHAR 型\)。  NULL 終端文字のための領域が含まれます。|LPDWORD|  
|`pwzProcessorArchitecture`|マニフェストから、アプリケーション配置のプロセッサ アーキテクチャを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwArchitectureBufferLength`|`pwzProcessorArchitecture` バッファーの長さを示す DWORD へのポインター \(WCHAR 型\)。|LPDWORD|  
|`pwzApplicationManifestCodebase`|マニフェストから、アプリケーション マニフェストのコードベースを指定する NULL で終わる文字列を受け取るバッファーへのポインター。|LPWSTR|  
|`pdwCodebaseBufferLength`|`pwzApplicationManifestCodebase` バッファーの長さを示す DWORD へのポインター \(WCHAR 型\)。|LPDWORD|  
|`pwzDeploymentProvider`|マニフェストから、配置プロバイダーを指定する NULL で終わる文字列を受け取るバッファーへのポインター \(存在する場合\)。  存在しない場合は、空の文字列が返されます。|LPWSTR|  
|`pdwProviderBufferLength`|`pwzProviderBufferLength` の長さを示す DWORD へのポインター。|LPDWORD|  
  
### 戻り値  
 処理が正常に終了した場合は、S\_OK を返します。それ以外の場合は、エラーを表す HRESULT を返します。  バッファーが小さすぎると、HRESULTFROMWIN32\(ERROR\_INSUFFICIENT\_BUFFER\) を返します。  
  
### 解説  
 ポインターは null 以外である必要があります。  `pcwzActivationUrl` と `pcwzPathToDeploymentManifest` を空にすることはできません。  
  
 アクティベーション URL のクリーンアップは、呼び出し元が保証します。  たとえば、必要なところにエスケープ文字を追加したり、クエリ文字列を削除したりします。  
  
 入力文字列の長さの制限は、呼び出し元が保証します。  たとえば、URL の最大長は 2 KB です。  
  
## LaunchApplication  
 配置 URL を使用して、アプリケーションを起動またはインストールします。  
  
### パラメーター  
  
|パラメーター|Description|種類|  
|------------|-----------------|--------|  
|`deploymentUrl`|配置マニフェストの URL を含む NULL で終わる文字列へのポインター。|LPCWSTR|  
|`data`|将来使用するために予約されています。  NULL であることが必要です。|LPVOID|  
|`flags`|将来使用するために予約されています。  0 にする必要があります。|DWORD|  
  
### 戻り値  
 処理が正常に終了した場合は、S\_OK を返します。それ以外の場合は、エラーを表す HRESULT を返します。  マネージ例外が発生すると、0x80020009 \(DISP\_E\_EXCEPTION\) を返します。  
  
## 参照  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>