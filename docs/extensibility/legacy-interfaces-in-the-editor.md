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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6f4c118ac9306bc533ba7cf62037a8255e9c42f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-interfaces-in-the-editor"></a>エディターでのレガシー インターフェイス
Visual Studio エディターは、従来のインターフェイスからアクセスできます。 Visual Studio SDK と呼ばれるアダプターが含まれています。 *shim*、新しいエディターとやり取りするこれらのインターフェイスを有効にします。 ただし、新しいエディター API を使用して従来のコードを更新することをお勧めします。 コードがパフォーマンスを向上させ、Windows Presentation Foundation (WPF) と Managed Extensibility Framework (MEF) などの新しいテクノロジを使用することができます。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[エディターにレガシ コードを改変](../extensibility/adapting-legacy-code-to-the-editor.md)|新しいエディターにコードを改変する方法について説明します。|  
|[エディターのアダプターで新しいまたは変更された動作](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|エディターの以前のバージョンのエディターのアダプターの動作がどのように異なるかについて説明します。|  
|[コア エディターの内部](../extensibility/inside-the-core-editor.md)|エディターの以前のバージョンのさまざまなコンポーネントをについて説明します。|  
|[レガシ API を使用してコア エディターをインスタンス化します。](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|従来の API を使用してコア エディターのインスタンスを作成する方法について説明します。|  
|[エディター ファクトリ](../extensibility/editor-factories.md)|エディター ファクトリを従来の API を使用する方法について説明します。|  
|[方法: エディター ファイルの種類の登録](../extensibility/how-to-register-editor-file-types.md)|ファイル名拡張子をエディターにリンクする方法について説明します。|  
|[チュートリアル: コア エディターを作成して、エディター ファイルの種類を登録します。](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|コア エディターを作成し、ファイル名拡張子をリンクする方法について説明します。|  
|[方法: エディターのコンテキストの提供](../extensibility/how-to-provide-context-for-editors.md)|エディターのコンテキストを提供する方法について説明します。|  
|[言語サービスとコア エディター](../extensibility/language-services-and-the-core-editor.md)|言語サービスと、エディターの間の相互作用をについて説明します。|  
|[レガシ API を使用してテキスト バッファーにアクセスします。](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|従来の API を使用して、テキスト バッファーにアクセスする方法について説明します。|  
|[レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|従来の API を使用して、テキスト ビューにアクセスする方法について説明します。|  
|[レガシ API を使用してコード ウィンドウをカスタマイズします。](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|従来の API を使用してコード ウィンドウをカスタマイズする方法について説明します。|  
|[レガシ API を使用してテキスト レイヤーにアクセスします。](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|従来の API を使用して、テキストの異なる層にアクセスする方法について説明します。|  
|[レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)|従来の API を使用してテキストのマーカーを追加する方法について説明します。|  
|[レガシ API を使用して、エディター コントロールとメニューをカスタマイズします。](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|従来の API を使用して、エディター コントロールをカスタマイズする方法について説明します。|  
|[管理の元に戻す/やり直しレガシ API を使用して](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|元に戻すを管理し、従来の API を使用して、再実行する方法について説明します。|  
|[方法: 検索の実装とメカニズムを置換](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|検索を管理し、従来の API を使用して、置換する方法について説明します。|  
|[方法: ファイル変更通知を抑制します。](../extensibility/how-to-suppress-file-change-notifications.md)|従来の API を使用して、ファイル変更通知を抑制する方法について説明します。|  
|[カスタム エディターとデザイナーを作成します。](../extensibility/creating-custom-editors-and-designers.md)|カスタム エディターとデザイナーを作成する方法について説明します。|  
|[従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)|カスタマイズ機能を提供する機能に関するドキュメントへのリンクを提供、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]コア エディターの言語サービスのサポートを追加します。|  
|[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md)|フォントおよび色を従来のインターフェイスを使用する方法について説明します。|
