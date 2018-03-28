---
title: コマンドの可用性 |Microsoft ドキュメント
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ee0f746b87fcc83e9967ea65be08b8f4b04f2e3f
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="command-availability"></a>利用可能なコマンド

Visual Studio のコンテキストでは、コマンドを使用できるを決定します。 コンテキストは、現在のプロジェクト、現在のエディター、読み込まれている Vspackage および統合開発環境 (IDE) の他の側面によって変更できます。

## <a name="command-contexts"></a>コマンドのコンテキスト

次のコマンドのコンテキストでは、最も一般的なです。

-   **IDE** IDE によって提供されるコマンドは常に利用できます。

-   **VSPackage**表示または非表示にするコマンドは、ときに Vspackage を定義できます。

-   **プロジェクト**プロジェクト コマンドは、現在選択されているプロジェクトにのみ表示されます。

-   **エディター**一度にアクティブにできるエディターの 1 つだけです。 アクティブなエディターからのコマンドを利用できます。 エディターは、言語サービスと緊密に動作します。 言語サービスは、関連付けられたエディターのコンテキストでそのコマンドを処理する必要があります。

-   **ファイルの種類**エディターは、1 つ以上の種類のファイルを読み込むことができます。 使用可能なコマンドは、ファイルの種類に応じて変更できます。

-   **アクティブなウィンドウ**最後のアクティブなドキュメント ウィンドウは、キー バインドのユーザー インターフェイス (UI) のコンテキストを設定します。 ただし、内部の Web ブラウザーのようなキー バインドのテーブルのあるツール ウィンドウでは、UI コンテキストが設定もできます。 HTML エディターなど、マルチタブのドキュメント ウィンドウ、タブごとに異なるコマンド コンテキストの GUID。 使用できるは常にツール ウィンドウは、登録後、**ビュー**メニュー。

-   **UI コンテキスト**UI コンテキストがの値で識別される、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>クラス、たとえば、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>ソリューションをビルドするときまたは<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>デバッガーがアクティブなときにします。 複数の UI コンテキストは、同時にアクティブにできます。

## <a name="defining-custom-context-guids"></a>カスタムのコンテキストの Guid を定義します。

適切なコマンドは、GUID が定義されていないコンテキスト場合、VSPackage のいずれかを定義し、アクティブまたは、コマンドの可視性を制御するために必要と非アクティブにすることをプログラムできます。

1.  呼び出してコンテキストの Guid を登録、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>メソッドです。

2.  呼び出してコンテキスト GUID の状態を取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>メソッドです。

3.  呼び出してコンテキスト Guid のオンとオフ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>メソッドです。

    > [!CAUTION]
    > VSPackage 影響を及ぼさないように既存のコンテキストの Guid に依存するその他の Vspackage のため確認してください。

## <a name="see-also"></a>関連項目

- [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)
- [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)