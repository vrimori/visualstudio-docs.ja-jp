---
title: エディターでの従来のインターフェイス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 340156463d2c4ec194ed70c0c8d74232574917ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842646"
---
# <a name="legacy-interfaces-in-the-editor"></a>エディターでのレガシー インターフェイス
Visual Studio エディターは、従来のインターフェイスからアクセスできます。 Visual Studio SDK と呼ばれるアダプタが含まれています。 *shim*、これらの新しいエディターと対話するインターフェイスを有効にします。 ただし、新しいエディターの API を使用して従来のコードを更新することをお勧めします。 コードのパフォーマンスが向上し、Windows Presentation Foundation (WPF) と Managed Extensibility Framework (MEF) などの新しいテクノロジを使用することができます。  

## <a name="related-topics"></a>関連トピック  

| タイトル | 説明 |
| - | - |
| [エディターにレガシ コードを改変します。](../extensibility/adapting-legacy-code-to-the-editor.md) | 新しいエディターにコードを改変する方法について説明します。 |
| [エディターのアダプターを搭載した新規または変更された動作](../extensibility/new-or-changed-behavior-with-editor-adapters.md) | エディターの以前のバージョンの動作のエディターのアダプターの違いについて説明します。 |
| [コア エディター](../extensibility/inside-the-core-editor.md) | エディターの以前のバージョンのさまざまなコンポーネントをについて説明します。 |
| [従来の API を使用して、コア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) | 従来の API を使用して、コア エディターのインスタンスを作成する方法について説明します。 |
| [エディター ファクトリ](../extensibility/editor-factories.md) | 従来の API でエディター ファクトリを使用する方法について説明します。 |
| [方法: エディターのファイルの種類を登録します。](../extensibility/how-to-register-editor-file-types.md) | エディターにファイル名拡張子をリンクする方法について説明します。 |
| [チュートリアル: コア エディターを作成し、エディター ファイルの種類を登録](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) | コア エディターを作成して、ファイル名拡張子をリンクする方法について説明します。 |
| [方法: エディターのコンテキストを提供します。](../extensibility/how-to-provide-context-for-editors.md) | エディターのコンテキストを提供する方法について説明します。 |
| [言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md) | 言語サービスとエディター間の相互作用をについて説明します。 |
| [従来の API を使用してテキスト バッファーへのアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) | 従来の API を使用して、テキスト バッファーにアクセスする方法について説明します。 |
| [従来の API を使用してアクセス テキスト ビュー](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) | 従来の API を使用して、テキスト ビューにアクセスする方法について説明します。 |
| [従来の API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) | 従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。 |
| [従来の API を使用してアクセス テキスト レイヤー](../extensibility/accessing-text-layers-by-using-the-legacy-api.md) | 従来の API を使用してテキストの異なる層にアクセスする方法について説明します。 |
| [テキスト マーカーを使用して、従来の API を使用しました。](../extensibility/using-text-markers-with-the-legacy-api.md) | 従来の API を使用してテキスト マーカーを追加する方法について説明します。 |
| [従来の API を使用して、エディター コントロールやメニューをカスタマイズします。](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md) | 従来の API を使用して、エディター コントロールをカスタマイズする方法について説明します。 |
| [元に戻すを管理し、従来の API を使用して再実行](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md) | 元に戻すを管理し、従来の API を使用して再実行する方法について説明します。 |
| [方法: 検索の実装し、メカニズムを置換](../extensibility/how-to-implement-the-find-and-replace-mechanism.md) | 検索の管理し、従来の API を使用して置き換える方法について説明します。 |
| [方法: ファイル変更通知を抑制します。](../extensibility/how-to-suppress-file-change-notifications.md) | 従来の API を使用して、ファイル変更通知を抑制する方法について説明します。 |
| [カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md) | カスタム エディターとデザイナーを作成する方法について説明します。 |
| [従来の言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md) | カスタマイズ機能を提供する機能に関するドキュメントへのリンクを提供します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターの言語サービスのサポートを追加します。 |
| [フォントおよび色を使用して、](../extensibility/using-fonts-and-colors.md) | 従来のインターフェイスで、フォントおよび色を使用する方法について説明します。 |
