---
title: レガシ言語サービスのコマンドをインターセプト |Microsoft Docs
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45f0084d060e9727f30ba39233ec5b92818d9205
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829886"
---
# <a name="intercepting-legacy-language-service-commands"></a>従来の言語サービスのコマンドの受信
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、テキスト ビューの処理とそれ以外の場合、言語サービス インターセプト コマンドがあることができます。 これは、テキスト ビューが管理していない言語固有の動作に役立ちます。 テキスト ビューに、言語サービスから 1 つまたは複数のコマンドのフィルターを追加することで、これらのコマンドを傍受できます。  
  
## <a name="getting-and-routing-the-command"></a>取得して、コマンドのルーティング  
 コマンド フィルターは、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>特定の文字のシーケンスまたはキーのコマンドを監視するオブジェクト。 コマンドの 1 つ以上のフィルターを 1 つのテキスト ビューと関連付けることができます。 各テキスト ビューでは、チェーンのコマンドのフィルターを保持します。 新しいコマンド フィルターを作成した後は、適切なテキスト ビューのチェーンに、フィルターを追加します。  
  
 呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドを<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>チェーンに、コマンドのフィルターを追加します。 呼び出すと<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コマンド フィルターが処理しないコマンドを渡せる別のコマンドのフィルターを返します。  
  
 コマンド処理のため、次のオプションがあります。  
  
- コマンドを処理し、チェーンの次のコマンドのフィルターにコマンドを渡します。  
  
- コマンドを処理し、次のコマンドのフィルターにコマンドを渡さないでください。  
  
- コマンドを処理しませんが、次のコマンドのフィルターにコマンドを渡します。  
  
- コマンドを無視します。 現在のフィルター処理しないと、次のフィルターに渡されません。  
  
  言語サービスを処理するコマンドの詳細については、次を参照してください。[言語サービス フィルターの重要なコマンド](../../extensibility/internals/important-commands-for-language-service-filters.md)します。

