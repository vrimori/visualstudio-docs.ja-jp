---
title: "デバッガーのコンテキスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 809f0f50ace62253371d4fd14425bb870a3be633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-contexts"></a>デバッガー コンテキスト
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグは、デバッグ エンジン (DE) 操作に同時にいくつかの異なるコンテキスト内で次のようにします。  
  
-   プログラムの実行のストリームの現在の場所を記述するコードのコンテキスト。  
  
-   ドキュメントのコンテキストまたは位置で、ソース ドキュメント内の現在位置をについて説明します。  
  
-   式の評価は行わコンテキストを記述する式の評価のコンテキスト。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コード コンテキスト](../../extensibility/debugger/code-context.md)  
 ここでコードが表現できない手順については、他の方法で、従来とは異なる言語ではなく現在の実行時のアーキテクチャでプログラムの命令ストリーム内のアドレスとして、コードのコンテキストについて説明します。  
  
 [ドキュメントの位置](../../extensibility/debugger/document-position.md)  
 Visual Studio の IDE に認識されているソース ファイル内の位置の抽象化を使用してデバッグにドキュメントの位置を定義します。  
  
 [ドキュメントのコンテキスト](../../extensibility/debugger/document-context.md)  
 説明で Visual Studio のデバッグ ソース ファイルに関連してどのようなドキュメントのコンテキストを表します。 シンボル ハンドラーがドキュメントのコンテキストに、コードのコンテキストをどのようにマップする方法についても説明します。  
  
 [式の評価のコンテキスト](../../extensibility/debugger/expression-evaluation-context.md)  
 Visual Studio での式の評価コンテキストに関する情報を提供します。 たとえば、スタック フレームに関連付けられている式の評価コンテキストは、ローカル変数、メソッドのパラメーター、およびクラス メンバーを評価するためのコンテキストを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッグの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
 [コンポーネントのデバッグ](../../extensibility/debugger/debugger-components.md)  
 デバッグ エンジン (DE)、式エバリュエーター (EE) およびシンボル ハンドラー (SH) を含む Visual Studio デバッグ コンポーネントの概要を示します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式を評価するなど、さまざまなデバッグ タスクへのリンクが含まれています。