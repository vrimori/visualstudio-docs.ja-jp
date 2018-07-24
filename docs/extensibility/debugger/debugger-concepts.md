---
title: デバッガーの概念 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e38c743ce7170e0842a3430c7b2aa190df94782b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203807"
---
# <a name="debugger-concepts"></a>デバッガーの概念
Visual Studio のデバッグ パッケージをビルドするには、パッケージの設計で使用されるアーキテクチャの概念を理解する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッグ セッション](../../extensibility/debugger/debug-session.md)  
 デバッグのアーキテクチャでは、セッションの役割について説明します。  
  
 [サーバー](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 定義抽象と物理の両方の用語で、アーキテクチャのデバッグの観点からどのようなサーバーは、します。  
  
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)  
 定義ポート サプライヤーは、デバッグのアーキテクチャの観点から。  
  
 [ポート](../../extensibility/debugger/ports.md)  
 定義デバッグのアーキテクチャの観点からどのようなポートとは。  
  
 [プロセス](../../extensibility/debugger/processes.md)  
 定義デバッグのアーキテクチャの観点からどのようなプロセスとは。  
  
 [プログラム ノード](../../extensibility/debugger/program-nodes.md)  
 デバッグ自体とで実行されているプロセスを特定できる方法を含めて、アーキテクチャの観点からプログラム ノードを定義します。  
  
 [プログラム](../../extensibility/debugger/programs.md)  
 デバッグのアーキテクチャの観点からプログラムを定義します。  
  
 [スレッド](../../extensibility/debugger/threads.md)  
 デバッグのアーキテクチャの観点からのスレッドの特性を定義します。  
  
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)  
 デバッグのアーキテクチャの観点からのスタック フレームを定義します。 スタック フレームは、スレッドの実行コンテキストを提供するスタックの抽象化です。  
  
 [モジュール](../../extensibility/debugger/modules.md)  
 アーキテクチャをデバッグ実行可能ファイルや DLL などのコードの物理コンテナーとしての観点から、モジュールを定義します。  
  
 [ブレークポイント](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 次の 3 つの種類のブレークポイントを定義します: 保留中、バインド、およびエラー-デバッグのアーキテクチャの観点から。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デバッグ エンジン (DE) が同時にして動作し、コード、ドキュメント、および式の評価のコンテキスト内で方法について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 デバッグ エンジン (DE)、式エバリュエーター (EE) シンボル ハンドラー (SH) など、Visual Studio デバッグ コンポーネントの概要を示します。  
  
 [タスクをデバッグします。](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。