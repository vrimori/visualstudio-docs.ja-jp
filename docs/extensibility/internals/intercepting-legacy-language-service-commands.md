---
title: "言語サービスのレガシのコマンドをインターセプトし、|Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73524ce47dfea2d30e44e51e97bf584a95a86482
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="intercepting-legacy-language-service-commands"></a>言語サービスのレガシのコマンドをインターセプトし、
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、テキスト ビューの処理とそれ以外の場合、言語サービス切片コマンドことができます。 これは、テキスト ビューが管理していない言語固有の動作に役立ちます。 テキスト ビューに、言語サービスから 1 つまたは複数のコマンドのフィルターを追加することによってこれらのコマンドをインターセプトすることができます。  
  
## <a name="getting-and-routing-the-command"></a>取得して、コマンドをルーティング  
 コマンドのフィルターは、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>特定の文字のシーケンスまたはキーのコマンドを監視するオブジェクト。 コマンドの 2 つ以上のフィルターを 1 つのテキスト ビューと関連付けることができます。 各テキスト ビューでは、チェーンのコマンドのフィルターを保持します。 新しいコマンド フィルターを作成した後は、適切なテキスト ビューのチェーンにフィルターを追加します。  
  
 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>チェーンに、コマンドのフィルターを追加します。 呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンド フィルターが処理しないコマンドを渡せる別のコマンド フィルターを返します。  
  
 次のコマンドの処理オプションがあります。  
  
-   コマンドを処理し、チェーンの次のコマンドのフィルターにコマンドを渡します。  
  
-   コマンドを処理し、次のコマンドのフィルターにコマンドを渡さないでください。  
  
-   コマンドを処理しないが、次のコマンドのフィルターにコマンドを渡します。  
  
-   コマンドを無視します。 現在のフィルターで処理しないし、次のフィルターには渡されない。  
  
 言語サービスが処理するどのコマンドの詳細については、次を参照してください。[言語サービスのフィルターの重要なコマンド](../../extensibility/internals/important-commands-for-language-service-filters.md)です。