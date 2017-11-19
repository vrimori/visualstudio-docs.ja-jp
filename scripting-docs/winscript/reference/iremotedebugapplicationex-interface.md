---
title: "IRemoteDebugApplicationEx インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3360cea0d1649348a795356ad827b32b6f8ebc19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationex-interface"></a>IRemoteDebugApplicationEx インターフェイス
実行中のアプリケーションを表します。 オペレーティング システム プロセスに対応する必要はありません。 通常、デバッガーでは、デバッグ用のアプリケーションが対象です。 プロセスをデバッグ マネージャーは、通常、アプリケーション オブジェクトを実装します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IRemoteDebugApplicationEx`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|ホスト アプリケーションのプロセス ID を返します。|  
|GetHostMachineName|ホスト アプリケーションが実行されているコンピューターの名前を返します。|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|デバッガーのローカライズ用の言語を設定します。|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|シングル ステップ モードにデバッガーを強制します。|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|中断コマンドを取り消します。|  
|SetProxyBlanketAndAddRef|Windows 95 ベース オペレーティング システムからのリモート デバッグとの互換性を確保するには、デバッガー オブジェクトのプロキシの COM セキュリティ情報を更新します。|  
|ReleaseFromSetProxyBlanket|SetProxyBlanketAndAddRef から AddRef をリリースします。|