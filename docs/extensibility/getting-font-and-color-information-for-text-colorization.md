---
title: フォントと色づけのテキストの色の情報の取得 |Microsoft Docs
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
ms.openlocfilehash: 49b1fbf18fb0dac23fcc55b7d9765dd4d1a88d32
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499700"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>テキストの色づけのフォントと色の情報を取得します。
レンダリングまたはユーザー インターフェイス (UI) 要素の色分けされたテキストを表示するプロセスは、プロジェクト、その技術、および開発者の環境設定の種類によって異なります。 **フォントおよび色**プロパティ ページには、設定が格納されます。

 色分けされたテキストを表示するほとんどの実装が必要な<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>表示設定の表示、取得、およびテキストを格納するは、インターフェイスを関連付けられているとします。

> [!NOTE]
>  コア エディターをカスタマイズする際に (サポートする、**テキスト EditorCategory**)、言語サービスでの色分け表示テクノロジを使用することをお勧めします。 詳細については、次を参照してください。[フォントと色の概要](../extensibility/font-and-color-overview.md)します。

## <a name="get-default-font-and-color-information"></a>既定のフォントと色の情報を取得します。
 すべての**フォントおよび色**でテキストを表示するすべてのウィンドウの設定を指定する必要があります、**表示項目**いずれかの**カテゴリ**します。 詳細については、次を参照してください。[フォントと色、環境オプション ダイアログ ボックス、](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)します。

VSPackage を色分けして表示、現在を取得する必要があります**フォントおよび色**設定します。 VSPackage では、そのニーズに応じて、次の方法で現在の設定を取得できます。

-   フォントおよびカラーの永続化メカニズムを使用して、ストアドまたは現在の状態を取得します。 詳細については、次を参照してください。[へのアクセスには、フォントおよび色の設定が格納されている](../extensibility/accessing-stored-font-and-color-settings.md)します。

-   使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスのインスタンスを取得するフォントと色のデータを提供するサービスの<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>もフォントおよびカラー プロバイダーが、VSPackage ではないです場合。

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> インターフェイスを実装します。

ポーリングによって得られた結果が最新の状態に日付は、使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>インターフェイスの取得メソッドを呼び出す前に、更新プログラムが必要なかどうかを決定する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>インターフェイス。

フォントと色の情報を取得した後、色付けを必要とする要素を識別するために表示されるテキストを解析します。 適切なフォントおよび色を使用して、ウィンドウで、テキストを表示します。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [使用してフォントとテキスト](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [色を調整します。](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (グラフィックス デバイス インターフェイス)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)