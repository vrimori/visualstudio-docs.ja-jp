---
title: デバッグ エンジン |Microsoft Docs
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
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf2335b907601bb17276b06ae1bef033a1641515
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733332"
---
# <a name="debug-engine"></a>デバッグ エンジン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッグ エンジン (DE) は、実行の制御やブレークポイントなど、式の評価などのデバッグ サービスを提供するには、インタープリターまたはオペレーティング システムで動作します。 デはデバッグ中のプログラムの状態を監視します。 これを行うには、デは、CPU または Api からは、ランタイムによって提供されるかどうか、いずれかの方法がサポートされているランタイムで使用することを使用します。  
  
 たとえば、共通言語ランタイム (CLR) は、ICorDebugXXX インターフェイスを介して実行中のプログラムを監視するためのメカニズムを提供します。 CLR をサポートする DE では、デバッグ中のマネージ コード プログラムを追跡するのに適切な ICorDebugXXX インターフェイスを使用します。 セッション デバッグ マネージャー (SDM)、このような情報を転送する状態の変更が通信して、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。  
  
> [!NOTE]
>  デバッグ エンジンでの実行とデバッグ対象のプログラム、システムは、特定のランタイムを対象とします。 CLR はマネージ コード用のランタイムと Win32 ランタイムは、ネイティブ Windows アプリケーション。 作成する言語が対象これら 2 つのランタイムのいずれかの場合[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]既に必要なデバッグ エンジンを提供します。 式エバリュエーターは、実装する必要があります。  
  
## <a name="debug-engine-operation"></a>デバッグ エンジンの操作  
 サービスの監視は、DE インターフェイスによって実装され、デバッグ パッケージを別の操作モード間の遷移が発生することができます。 詳細については、次を参照してください。[操作モード](../../extensibility/debugger/operational-modes.md)します。 通常は実行時環境ごとに 1 つだけ DE 実装です。  
  
> [!NOTE]
>  TRANSACT-SQL の別個の DE 実装中と[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]、VBScript と[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]単一 DE を共有します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] デバッグできるように 2 つの方法のいずれかを実行するエンジンのデバッグ: いずれかと同じプロセスで、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]シェル、または対象のプログラムと同じプロセスはデバッグ中です。 後者の形式は、デバッグ中のプロセスが実際には、インタープリターで実行されているスクリプトとデバッグ エンジンでは、スクリプトを監視するには、インタープリターの詳細な知識が必要に通常発生します。 この場合は、インタープリターは、ランタイムでは実際にはデバッグ エンジンでは、特定のランタイムの実装です。 さらに、1 つのドイツの実装は、(たとえば、リモート デバッグ) プロセスとマシンの境界を越えて分割されることができます。  
  
 DE 公開、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッグのインターフェイス。 すべての通信は、COM 経由 プロセスで、アウト プロセス、または別のコンピューター上に、DE が読み込まれるかどうかは、コンポーネントの通信は影響しません。  
  
 デは、その特定の実行時の式の構文を理解する DE を有効にする、式エバリュエーターのコンポーネントで動作します。 言語コンパイラによって生成されたシンボリック デバッグ情報にアクセスするシンボル ハンドラー コンポーネントでも、DE が機能します。 詳細については、次を参照してください。[式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)と[シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [シンボル プロバイダー](../../extensibility/debugger/symbol-provider.md)

