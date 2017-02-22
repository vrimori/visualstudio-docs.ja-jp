---
title: "エンジンをデバッグします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジン"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# エンジンをデバッグします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

実行制御ブレークポイントや式の評価などのデバッグ サービスを提供するインタープリターまたはオペレーティング システムのデバッグ エンジン \(DE\) を使用します。  DE でプログラムの状態を監視する必要があります。  の CPU またはランタイムによって提供される API かどうかをするにはこれを実現するにはメソッドがサポートされているランタイムに使用できる DE を使用します。  
  
 たとえば共通言語ランタイムは \(CLR\) ICorDebugXXX のインターフェイスを通じて実行中のプログラムを監視する機能を提供します。  CLR デバッグをサポートする DE はマネージ コードでプログラムを追跡するために ICorDebugXXX の適切なインターフェイスを使用します。  次に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE にこのような情報を転送する \(SDM\) メッセージのデバッグ セッション状態の変化を通知します。  
  
> [!NOTE]
>  デバッグ エンジンは特定のランタイムデバッグ実行するプログラムつまりシステムを対象とします。  CLR がマネージ コードの実行時にランタイムがネイティブ Win32 Windows アプリケーション用です。  作成した言語が既に指定する場合は必要なデバッグ エンジンはこれら二つのランタイムの 1[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 対象とすることができます。  ユーザーが実行する必要があるのは式エバリュエーターだけです。  
  
## デバッグ エンジンの操作  
 サービスは監視します interfaces を通じて実行してさまざまなオペレーショナル モードの切り替えにデバッグのパッケージが発生することがあります。  詳細については、「[操作モード](../../extensibility/debugger/operational-modes.md)」を参照してください。  ランタイム環境に対してだけ1 人の de\-DE implementation があります。  
  
> [!NOTE]
>  Transact\-SQL の de\-DE implementations と [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] ですがVBScript や [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] はde\-DE を共有します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 2 種類の方法の 1 つがを実行するには有効なデバッグ エンジンをのデバッグ: シェルと同じ[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロセスまたは同じプロセス デバッグ対象プログラム。  後者の形式は通常デバッグ プロセスがインタープリターで実行するスクリプトのデバッグ エンジンはスクリプトを監視するにはインタープリターには密接な知識が必要ですが発生します。  はインタープリターが実際にランタイムこの場合は注意してください ; デバッグ エンジンは特定のランタイムの実装です。  さらに単一 DE の実装はプロセスとマシン境界 \(たとえばリモート デバッグ\) に分割できます。  
  
 DE はインターフェイスをデバッグ   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を公開します。  すべての通信はCOM であります。  DE は読み込みプロセスは別のコンピューターのプロセスか構成の通信に影響を与えません。  
  
 DE は式エバリュエーターのコンポーネントを式の構文を理解して特定の実行時の de\-DE を有効にします。  DE コンポーネントをシンボル ハンドラーは言語コンパイラによって生成されるシンボリック デバッグ情報にアクセスするために使用します。  詳細については、「[式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)」および「[シンボルのプロバイダー](../../extensibility/debugger/symbol-provider.md)」を参照してください。  
  
## 参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [シンボルのプロバイダー](../../extensibility/debugger/symbol-provider.md)