---
title: フォントと色の使用 |Microsoft Docs
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
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b49c5172a75e0abec8084892346a2fb0da877b81
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729600"
---
# <a name="using-fonts-and-colors"></a>フォントと色の使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]フォントおよび色を使用してテキストを表示するサポートを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [フォントと色の概要](../extensibility/font-and-color-overview.md)  
 テキストのフォントと色の設定について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]統合開発環境 (IDE) です。 カテゴリとアイテムの表示の概念を説明し、Vspackage とコア エディターのテキスト属性を使用する方法について説明します。  
  
 [テキストに色づけするためのフォントと色の情報の取得](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 管理 Vspackage でテキストの色づけを実装するためのガイドラインを提供します。**カテゴリ**以外**テキスト エディター**します。  
  
 [格納されたフォントと色の設定へのアクセス](../extensibility/accessing-stored-font-and-color-settings.md)  
 現在のフォントと色を説明します。 設定の保存、取得と適用されることができます。  
  
 [カスタム カテゴリと表示項目の実装](../extensibility/implementing-custom-categories-and-display-items.md)  
 使用されるウィンドウを作成および使用できる、独自の基本的な手順について説明します**アイテムを表示**と**カテゴリ**テキストの表示をサポートするためにします。  
  
 このアプローチを実装するために VSPackage が必要です、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスと関連するインターフェイス。  
  
 [方法: 組み込みのフォントおよび色のスキーマにアクセスする](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 定義して組み込みのフォントや色を使用して、カテゴリを登録し、システム指定のフォントと色の使用を開始する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 インスタンスを提供、`IVsFontAndColorDefaults`または<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>インターフェイスに表示された特定の項目に対応する、**設定を表示する**の一覧で、**フォントおよび色**のページ**オプション** ダイアログ ボックス。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 により、IDE をサポートするために VSPackage**フォントおよび色**ウィンドウまたは UI コンポーネントの既定のフォントと色を定義することでページ。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 使用される機構を提供します。 表示項目のグループ - 2 つ以上のカテゴリの和集合を表すスーパー カテゴリを指定できますフォントと色のサポートを提供する VSPackage は。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 フォントおよび色のデータを取得したり、レジストリに保存するために VSPackage を使用できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 フォントおよび色の設定でのフォントと色の変更に関する情報を使用している Vspackage に通知します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 メソッドによって使用される入力と出力データを操作するためのツールを提供します、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **フォントおよびカラー**メカニズム。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 フォントおよび色の設定のキャッシュを制御します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)  
 Vspackage が言語サービスを使用して、カスタマイズする方法について説明します、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディター。  
  
 [カスタム エディターでの構文の色分け表示](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 方法、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディターでは、言語サービスを使用して、構文の色分けを実装します。  
  
 [Visual Studio の他の部分の拡張](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] サービスを使用して、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の他の部分に相当する UI 要素を作成する方法について説明します。

