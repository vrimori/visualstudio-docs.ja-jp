---
title: 選択範囲と、IDE で通貨 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c58cb08f82b10970424600843b0fedcf477fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131273"
---
# <a name="selection-and-currency-in-the-ide"></a>選択範囲と、IDE の通貨
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) の保持の選択を使用して、ユーザーの情報がオブジェクトに現在選択されている*コンテキスト*です。 選択コンテキスト、Vspackage が、2 つの方法での追跡の通貨でパーツを受け取ることができます。  
  
-   によって、通貨情報を IDE に Vspackage を伝達します。  
  
-   IDE 内でユーザーの現在アクティブな選択を監視します。  
  
## <a name="selection-context"></a>選択コンテキスト  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE グローバルの追跡、独自のグローバルの選択コンテキスト オブジェクトで IDE 通貨です。 次の表は、選択コンテキストを構成する要素を示しています。  
  
|要素|説明|  
|-------------|-----------------|  
|現在の階層|通常、現在のプロジェクトです。NULL の現在の階層では、全体として、ソリューションが最新であることを示します。|  
|現在のアイテム Id|現在の階層内で選択した項目選択した複数のプロジェクトのウィンドウである場合は、複数の現在の項目があります。|  
|現在の `SelectionContainer`|[プロパティ] ウィンドウがプロパティを表示する必要があります 1 つまたは複数のオブジェクトが保持されます。|  
  
 さらに、環境には、次の 2 つのグローバル リストが保持されます。  
  
-   アクティブな UI コマンド識別子の一覧  
  
-   現在アクティブな要素の型の一覧。  
  
### <a name="window-types-and-selection"></a>ウィンドウの種類と選択  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は 2 つの一般的な種類に windows を編成します。  
  
-   階層型の windows  
  
-   ツールとドキュメント ウィンドウなどのフレーム ウィンドウ  
  
 IDE は、これらのウィンドウの種類ごとに異なる方法で通貨を追跡します。  
  
 最も一般的なプロジェクトの種類 ウィンドウは、ソリューション エクスプ ローラー、IDE を制御します。 プロジェクトの種類 ウィンドウは、グローバルな階層と、グローバルの選択コンテキストの ItemID を追跡し、ウィンドウが現在の階層を決定する、ユーザーの選択に依存しています。 プロジェクトの種類の windows の場合、環境は、グローバル サービスを提供<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>を通じて、どの Vspackage が開いている要素の現在の値を監視できます。 プロパティの参照、環境では、このグローバル サービスによって左右されます。  
  
 フレーム ウィンドウ、その一方を使用して、DocObject フレーム ウィンドウ内でプッシュ SelectionContext 値 (階層/ItemID/SelectionContainer 進める)。 である必要があります。 フレーム ウィンドウは、サービスを使用して<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>この目的のためです。 DocObject は選択コンテナーの値のみをプッシュできる階層をローカルの値はそのままおよび ItemID 変更せずは MDI 子ドキュメントの一般的なことです。  
  
### <a name="events-and-currency"></a>イベントと通貨  
 通貨の環境の概念に影響する 2 種類のイベントが発生する可能性があります。  
  
-   グローバル レベルに反映されますが、ウィンドウ フレームの選択コンテキストを変更するイベントです。 この種類のイベントの例には、開いているグローバル ツール ウィンドウまたは開いているプロジェクトの種類のツール ウィンドウは、開いている MDI 子ウィンドウが含まれます。  
  
-   トレース ウィンドウ フレームの選択コンテキスト内で要素を変更するイベントです。 例についてには、DocObject 内の選択範囲を変更するか、プロジェクトの種類 ウィンドウで選択を変更が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)   
 [ユーザーへのフィードバック](../../extensibility/internals/feedback-to-the-user.md)