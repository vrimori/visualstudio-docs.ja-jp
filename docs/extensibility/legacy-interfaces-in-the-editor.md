---
title: "従来のインターフェイスをエディターで |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a9d09c452fb6d03f7f5072e34813c3757455f96a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-interfaces-in-the-editor"></a>エディターでの従来のインターフェイス
Visual Studio エディターは、従来のインターフェイスからアクセスできます。 Visual Studio SDK と呼ばれるアダプタが含まれています。 *shim*、新しいエディターと対話するこれらのインターフェイスを有効にします。 ただし、新しいエディター API を使用して従来のコードを更新することをお勧めします。 コードがパフォーマンスを向上させ、Windows Presentation Foundation (WPF) および Managed Extensibility Framework (MEF) などの新しいテクノロジを使用することができます。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[エディターにレガシ コードを改変.](../extensibility/adapting-legacy-code-to-the-editor.md)|新しいエディターにコードを改変する方法について説明します。|  
|[エディターのアダプターで新しいまたは変更された動作](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|エディターのアダプターの動作の違いを以前のバージョンのエディターについて説明します。|  
|[コア エディター内](../extensibility/inside-the-core-editor.md)|エディターの以前のバージョンのさまざまなコンポーネントをについて説明します。|  
|[レガシ API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|従来の API を使用して、コア エディターのインスタンスを作成する方法について説明します。|  
|[エディター ファクトリ](../extensibility/editor-factories.md)|従来の API でエディター ファクトリを使用する方法について説明します。|  
|[方法: エディター ファイルの種類の登録](../extensibility/how-to-register-editor-file-types.md)|ファイル名拡張子をエディターにリンクする方法について説明します。|  
|[チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|コア エディターを作成し、ファイル名拡張子をリンクする方法について説明します。|  
|[方法: エディターのコンテキストを指定](../extensibility/how-to-provide-context-for-editors.md)|エディターのコンテキストを提供する方法について説明します。|  
|[言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)|言語サービスと、エディターの間の相互作用をについて説明します。|  
|[レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|従来の API を使用してテキスト バッファーにアクセスする方法について説明します。|  
|[レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|従来の API を使用して、テキスト ビューにアクセスする方法について説明します。|  
|[レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。|  
|[レガシ API を使用してテキストのレイヤーにアクセスします。](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|従来の API を使用して、テキストのさまざまなレイヤーにアクセスする方法について説明します。|  
|[レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)|従来の API を使用してテキスト マーカーを追加する方法について説明します。|  
|[レガシ API を使用して、エディター コントロールやメニューをカスタマイズします。](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|従来の API を使用して、エディター コントロールをカスタマイズする方法について説明します。|  
|[管理元に戻すと、レガシ API を使用して再実行](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|元に戻すを管理し、従来の API を使用して再実行する方法について説明します。|  
|[方法: 検索の実装とメカニズムを置換](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|検索を管理し、従来の API を使用して、置換する方法について説明します。|  
|[方法: ファイル変更通知を抑制します。](../extensibility/how-to-suppress-file-change-notifications.md)|従来の API を使用してファイル変更通知を抑制する方法について説明します。|  
|[カスタム エディターとデザイナーの作成](../extensibility/creating-custom-editors-and-designers.md)|カスタム エディターおよびデザイナーを作成する方法について説明します。|  
|[従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)|カスタマイズ機能を提供する機能に関するドキュメントへのリンクを提供、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターの言語サービスのサポートを追加します。|  
|[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md)|従来のインターフェイスで、フォントおよび色を使用する方法について説明します。|