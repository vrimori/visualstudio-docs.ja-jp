---
title: "デバッガーの概念 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e928d396db2029bc4d2e659c869fd74e0df3191
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-concepts"></a>デバッガーの概念
Visual Studio デバッグ パッケージをビルドするには、パッケージの設計で使用されるアーキテクチャの概念を理解する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッグ セッション](../../extensibility/debugger/debug-session.md)  
 デバッグのアーキテクチャでは、セッションの役割について説明します。  
  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 定義抽象と物理の両方の条件で、アーキテクチャのデバッグの観点からは、どのようなサーバーです。  
  
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)  
 定義ポート サプライヤーは、デバッグのアーキテクチャの観点からです。  
  
 [ポート](../../extensibility/debugger/ports.md)  
 定義デバッグ アーキテクチャの観点からは、どのようなポートです。  
  
 [プロセス](../../extensibility/debugger/processes.md)  
 定義デバッグ アーキテクチャの観点からは、どのようなプロセスです。  
  
 [プログラム ノード](../../extensibility/debugger/program-nodes.md)  
 デバッグ自体とで実行されているプロセスを特定できる方法を含むアーキテクチャの観点からプログラム ノードを定義します。  
  
 [プログラム](../../extensibility/debugger/programs.md)  
 デバッグのアーキテクチャの観点からプログラムを定義します。  
  
 [スレッド](../../extensibility/debugger/threads.md)  
 デバッグのアーキテクチャの観点からスレッドの特性を定義します。  
  
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)  
 デバッグのアーキテクチャの観点からのスタック フレームを定義します。 スタック フレームは、スレッドの実行コンテキストを提供するスタックの抽象化です。  
  
 [モジュール](../../extensibility/debugger/modules.md)  
 アーキテクチャをデバッグする実行可能ファイルまたは DLL などのコードの物理的なコンテナーとしての観点から、モジュールを定義します。  
  
 [ブレークポイント](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 次の 3 つの種類のブレークポイントを定義-保留中のバインド、およびエラー-デバッグ アーキテクチャの観点からです。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デバッグ エンジン (DE) の動作方法に同時にコード、ドキュメント、および式の評価のコンテキスト内でについて説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 デバッグ エンジン (DE)、式エバリュエーター (EE) シンボル ハンドラー (SH) など、Visual Studio デバッグ コンポーネントの概要を示します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式を評価するなど、さまざまなデバッグ タスクへのリンクが含まれています。