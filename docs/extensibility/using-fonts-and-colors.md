---
title: "フォントおよび色を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>フォントおよび色を使用します。
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]フォントおよび色を使用してテキストを表示するサポートを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [フォントと色の概要](../extensibility/font-and-color-overview.md)  
 テキストのフォントと色の設定について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 カテゴリとアイテムの表示の概念を紹介し、Vspackage とコア エディターのテキスト属性を使用する方法について説明します。  
  
 [フォントとテキスト彩色の色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 管理する Vspackage でテキストの色づけを実装するためのガイドラインを提供**カテゴリ**以外の**テキスト エディター**です。  
  
 [ストアドのフォントおよび色の設定にアクセスします。](../extensibility/accessing-stored-font-and-color-settings.md)  
 現在のフォントと色を説明します。 設定の保存、取得と適用されることができます。  
  
 [カスタム カテゴリと 表示項目を実装します。](../extensibility/implementing-custom-categories-and-display-items.md)  
 これによって、ウィンドウ作成および使用できますの独自の基本的な手順について説明します**アイテムを表示**と**カテゴリ**テキストの表示をサポートするためにします。  
  
 このアプローチを実装する VSPackage が必要です、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスと関連するインターフェイスです。  
  
 [方法: 組み込みのフォントと配色へのアクセス](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 定義して組み込みのフォントおよび色 を使用して、カテゴリを登録し、システム指定のフォントおよび色の使用を開始する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 インスタンスを提供、`IVsFontAndColorDefaults`または<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>インターフェイスに表示された特定の項目に対応する、**設定を表示する**一覧に、**フォントおよび色**のページ**オプション** ダイアログ ボックス。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 により、IDE をサポートするために VSPackage**フォントおよび色**ウィンドウまたは UI コンポーネントの既定のフォントと色を定義することによってページ。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 機構を提供するフォントと色のサポートは表示項目のグループ - 2 つまたは複数のカテゴリの和集合を表すスーパー カテゴリを指定できますを提供する VSPackage です。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 フォントおよび色のデータを取得またはレジストリに保存する VSPackage を有効にします。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 フォントと色の設定に加えられた変更についてのフォントと色を使用している Vspackage に通知します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 メソッドによって使用される入力と出力のデータを操作するためのツールを提供、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **フォントおよびカラー**メカニズムです。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 フォントおよび色の設定のキャッシュを制御します。  
  
## <a name="related-sections"></a>関連項目  
 [従来の言語サービスの開発](../extensibility/internals/developing-a-legacy-language-service.md)  
 Vspackage が言語サービスを使用して、カスタマイズする方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターです。  
  
 [カスタム エディターでの構文の色分け表示](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 方法、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターでは、言語サービスを使用する構文の色分けを実装します。  
  
 [Visual Studio の他の部分の拡張](../extensibility/extending-other-parts-of-visual-studio.md)  
 使用する方法について説明します[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の残りの部分に一致する UI 要素を作成するサービス[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。