---
title: "IRemoteDebugApplicationEx インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx インターフェイス"
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx インターフェイス
実行中のアプリケーションを表します。  これは、オペレーティング システム プロセスに対応する必要はありません。  通常、デバッグ対象のアプリケーションを対象とします。  プロセス デバッグ マネージャーは、通常、アプリケーション オブジェクトを実装します。  
  
 `IUnknown` から継承するメソッドに加え、`IRemoteDebugApplicationEx` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|ホスト アプリケーションのプロセス ID を返します。|  
|GetHostMachineName|ホスト アプリケーションが実行されているコンピューターの名前を返します。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|デバッガーのローカリゼーションの言語を設定します。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|シングル ステップ実行モードにデバッガーを強制します。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|中断コマンドをキャンセルします。|  
|SetProxyBlanketAndAddRef|Windows 95 ベースのオペレーティング システムからリモート デバッグで互換性を確保するデバッガーのオブジェクトのプロキシの更新の COM セキュリティ情報。|  
|ReleaseFromSetProxyBlanket|SetProxyBlanketAndAddRef からリリース AddRef。|