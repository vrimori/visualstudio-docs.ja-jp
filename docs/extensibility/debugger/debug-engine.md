---
title: "デバッグ エンジンが |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2db510e81231f7802d686b21a977c271a66c5d79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debug-engine"></a>デバッグ エンジン
デバッグ エンジン (DE) は、実行の制御やブレークポイントなどの式の評価などのデバッグ サービスを提供する、インタープリターまたはオペレーティング システムで動作します。 デはデバッグ中のプログラムの状態を監視します。 これを実現するには、DE は、CPU とは Api からは、ランタイムによって提供されるかどうかは、任意のメソッドはランタイムではサポートされている、使用を使用します。  
  
 たとえば、共通言語ランタイム (CLR) は、ICorDebugXXX インターフェイスによって実行中のプログラムを監視するメカニズムを提供します。 CLR をサポートする DE では、デバッグ中のマネージ コード プログラムを追跡するのに ICorDebugXXX の適切なインターフェイスを使用します。 このような情報を転送するセッションのデバッグ マネージャー (SDM) に状態の変更が通信して、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
> [!NOTE]
>  デバッグ エンジンでの実行とデバッグ対象のプログラム、システムは、特定のランタイムをターゲットです。 CLR は、マネージ コード用のランタイムと、Win32 ランタイムは、ネイティブ Windows アプリケーション用。 言語を作成するには、これら 2 つのランタイムのいずれかの対象ことができる場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]既に必要なデバッグ エンジンを提供します。 実装するためには、式エバリュエーターです。  
  
## <a name="debug-engine-operation"></a>デバッグ エンジンの操作  
 サービスの監視は、DE インターフェイスを通じては実装され、デバッグにパッケージを別の操作モードの間の遷移が発生することができます。 詳細については、次を参照してください。[の操作モード](../../extensibility/debugger/operational-modes.md)です。 実行時環境ごとに 1 つだけ DE 実装は通常です。  
  
> [!NOTE]
>  TRANSACT-SQL の別個の DE 実装があるときに、 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]、VBScript と[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]単一 DE を共有します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ デバッグ エンジンを 2 つの方法のいずれかを実行する: と同じプロセスのいずれか、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェル、またはターゲット プログラムと同じプロセスはデバッグ中です。 後者の形式は、デバッグ中のプロセスが実際には、インタープリターで実行されているスクリプトと、デバッグ エンジンでは、スクリプトを監視するために、インタープリターの詳細な知識が必要に通常発生します。 この例では、インタープリターは、実際には、実行時です。デバッグ エンジンは、特定のランタイムの実装です。 さらに、(たとえば、リモート デバッグ) プロセスやコンピューターの境界を越えて 1 つ DE の実装を分割できます。  
  
 DE 公開、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグのインターフェイスです。 すべての通信は、COM 経由 プロセスで、アウト プロセス、または別のコンピューター上に、DE が読み込まれるかどうかは、コンポーネントの通信は影響しません。  
  
 デは、その特定の実行時の式の構文を理解する DE を有効にする、式エバリュエーターのコンポーネントと連携します。 デは、言語コンパイラによって生成されたシンボリック デバッグ情報にアクセスするシンボル ハンドラー コンポーネントとも連携することができます。 詳細については、次を参照してください。[式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)と[シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)です。  
  
## <a name="see-also"></a>関連項目  
 [デバッガー コンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)