---
title: フォントとテキスト彩色の色の情報を取得する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c86e37d6d7da9da0a6b0978770bf7d7564fa19c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>フォントとテキスト彩色の色の情報を取得します。
レンダリングまたはユーザー インターフェイス (UI) 要素の色分けされたテキストを表示するプロセスは、プロジェクト、テクノロジ、および developer の基本設定の種類によって異なります。 **フォントおよび色**プロパティ ページの設定を保存します。

 色分けされたテキストを表示するほとんどの実装が必要な<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>表示設定の表示、取得、およびテキストを格納するためのインターフェイスを関連付けられているとします。

> [!NOTE]
>  コア エディターをカスタマイズするとき (がサポートする、**テキスト EditorCategory**)、言語サービスでは、色分けテクノロジを使用することをお勧めします。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)です。

## <a name="getting-default-font-and-color-information"></a>既定のフォントと色の情報を取得します。
 すべての**フォントおよび色**でテキストを表示するすべてのウィンドウの設定を指定する必要があります、**表示項目**いずれかの**カテゴリ**です。 詳細については、次を参照してください。[フォントおよび色のオプション ダイアログ ボックス](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)です。

VSPackage、色分けして表示する現在を取得する必要があります**フォントおよび色**設定します。 VSPackage では、そのニーズに応じて、次の方法で現在の設定を取得できます。

-   フォントおよびカラーの永続化メカニズムを使用して、ストアドまたは現在の状態を取得します。 詳細については、次を参照してください。[にアクセスする格納されているフォントと色の設定](../extensibility/accessing-stored-font-and-color-settings.md)です。

-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>のインスタンスを取得するフォントと色のデータを提供するサービスのインターフェイス<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>もフォントおよびカラー プロバイダーが、VSPackage ではない場合は、します。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> インターフェイスを実装します。

確実にポーリングによって取得される結果は最新の状態に日付を使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得方法を呼び出す前に、更新が必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイスです。

フォントと色の情報を取得した後、色付けを必要とする要素を識別する表示されるテキストを解析します。 適切なフォントと色を使用して、ウィンドウでテキストを表示します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [フォントとテキストの使用](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [カラーを使用します。](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (グラフィックス デバイス インターフェイス)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)