---
title: コマンドの可用性 |Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac9a172ee2cb7a117a1d9b63c4f1fef9f631952
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915871"
---
# <a name="command-availability"></a>利用可能なコマンド

Visual Studio のコンテキストでは、コマンドが使用可能な判断します。 コンテキストによっては、現在のプロジェクト、現在のエディター、読み込まれる Vspackage および統合開発環境 (IDE) の他の側面を変更できます。

## <a name="command-contexts"></a>コマンドのコンテキスト

次のコマンドのコンテキストは、最も一般的です。

- IDE:IDE で提供されるコマンドは常に使用できます。

- VSPackage:Vspackage では、表示または非表示にするコマンドが場合を定義できます。

- プロジェクト:プロジェクトのコマンドは、現在選択されているプロジェクトに対してのみ表示されます。

- エディター:一度にアクティブにできるエディターの 1 つだけです。 アクティブなエディターからのコマンドを利用できます。 エディターは、言語サービスと密接に連携します。 言語サービスでは、関連付けられているエディターのコンテキストでは、そのコマンドを処理する必要があります。

- ファイルの種類:エディターでは、1 つ以上の種類のファイルを読み込むことができます。 使用可能なコマンドは、ファイルの種類に応じて変更できます。

- アクティブなウィンドウ:最後のアクティブなドキュメント ウィンドウは、キー バインドのユーザー インターフェイス (UI) のコンテキストを設定します。 ただし、内部 web ブラウザーのようなキー バインドのテーブルのあるツール ウィンドウでは、UI コンテキストが設定もできます。 HTML エディターなどの複数タブ付きドキュメント ウィンドウ、各タブは別のコマンド コンテキストの GUID を持っています。 常にで使用できるツール ウィンドウは、登録後、**ビュー**メニュー。

- UI コンテキスト:UI コンテキストがの値によって識別される、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>クラス、たとえば、<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>ソリューションが構築されるときにまたは<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>デバッガーがアクティブな場合。 同時にアクティブにできる複数の UI コンテキストです。

## <a name="define-custom-context-guids"></a>カスタム コンテキストの Guid を定義します。

適切なコマンドは、GUID が定義されていないコンテキスト場合、VSPackage のいずれかを定義およびアクティブまたはコマンドの表示を制御する必要に応じて非アクティブにすることをプログラムできます。

1.  呼び出してコンテキストの Guid を登録、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A>メソッド。

2.  呼び出してコンテキストの GUID の状態を取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>メソッド。

3.  呼び出してコンテキストの Guid のオンとオフ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A>メソッド。
   
> [!CAUTION]
> 確認して、VSPackage 影響を及ぼさないように既存のコンテキストの Guid の他の Vspackage がそれらに依存している可能性があります。

## <a name="see-also"></a>関連項目

- [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)
- [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)