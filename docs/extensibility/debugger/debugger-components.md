---
title: "デバッガーのコンポーネント | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ [Visual Studio]、[コンポーネント"
  - "デバッグ [Visual Studio SDK] のコンポーネント"
  - "[デバッグ SDK] コンポーネントのデバッグ"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# デバッガーのコンポーネント
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッガーではVSPackage として実装され全体的なデバッグ セッションを管理します。  デバッグ セッションは次の要素から構成されます :  
  
-   **デバッグのパッケージ :** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッガーはデバッグと同じユーザー インターフェイスを提供します。  
  
-   **デバッグ セッションのマネージャー \(SDM\):** さまざまなデバッグ エンジンの管理に [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッガーに一貫したプログラミング インターフェイスを提供します。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって実装されます。  
  
-   **プロセス デバッグ : マネージャー \(PDM\)** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] で実行中のすべてのインスタンスの場合なる可能性があるかデバッグ中のすべてのプログラムの一覧管理します。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって実装されます。  
  
-   **デバッグ エンジン \(DE\):** SDM と PDM に伝え実行中のプログラムをデバッグするプログラムの状態を監視する必要があります。およびプログラムのメモリおよび変数の状態のリアルタイムの解析を提供する式エバリュエーターとシンボルのプロバイダーと対話します。  これは独自のランタイムをサポートするサードパーティ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] としてサポートする言語に対して実行されます。\)  
  
-   **式エバリュエーター \(EE\):** プログラムが特定のポイントで停止したユーザーが指定する動的評価の変数と式をサポートします。  これは独自の言語をサポートするサードパーティ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] としてサポートする言語に対して実行されます。\)  
  
-   **シンボルのプロバイダー \(SP\):** またわかりやすい情報を提供できるようにシンボル ハンドラーをマップします。ただしプログラムの実行中のインスタンスでプログラムのデバッグ シンボルを呼び出しています \(ソース・コード レベルのデバッグや式の評価など\)。  これは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に共通言語ランタイム \(CLR \[入力\] シンボルとプログラム データベース \(PDB \[\] シンボル ファイル形式の場合\) およびデバッグ情報を格納する独自のメソッドが一部のサードパーティによって実装されます。  
  
 次の図はVisual Studio デバッガーで次の要素との関係を示します。  
  
 ![コンポーネント デバッグの概要](~/extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## このセクションの内容  
 [パッケージをデバッグします。](../../extensibility/debugger/debug-package.md)  
 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のシェルおよびハンドル実行中のすべてのパッケージのデバッグについて説明します。  
  
 [プロセスのデバッグ マネージャー](../../extensibility/debugger/process-debug-manager.md)  
 デバッグするプロセスの管理者である PDM 機能の概要について説明します。  
  
 [セッションのデバッグ マネージャー](../../extensibility/debugger/session-debug-manager.md)  
 IDE でデバッグ セッションの統一されたビューを提供する SDM を定義します。  SDM は de\-DE を管理します。  
  
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)  
 DE が提供するデバッグ サービスについて説明します。  
  
 [操作モード](../../extensibility/debugger/operational-modes.md)  
 IDE で使用できる 3 つモードの概要を提供します : デザイン モードおよび実行モードおよび中断モード。  遷移の機能も説明します。  
  
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)  
 実行時に EE の目的について説明します。  
  
 [シンボルのプロバイダー](../../extensibility/debugger/symbol-provider.md)  
 実装でシンボルのプロバイダーは変数や式を評価する方法について説明します。  
  
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 ビジュアライザーの型とカスタム ビューアーはです。ロールを式エバリュエーターの両方を持つ任意のサポートについて説明します。  
  
## 関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグの主要なアーキテクチャの概念について説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 DE コードがドキュメント式の評価のコンテキスト内で同時に動作するかを示しています。  それに関連する 3 種類のコンテキスト位置位置または値ごとについて説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動し式を評価などのさまざまなデバッグ タスクへのリンクが含まれます。  
  
## 参照  
 [作業の開始](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)