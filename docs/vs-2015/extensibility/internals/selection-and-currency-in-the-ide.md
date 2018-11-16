---
title: 選択と、IDE で通貨 |Microsoft Docs
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
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45fc57bf2d5763527f9f8c2c6d8d22ca1d6369f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786744"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE での選択と通貨
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]選択を使用してユーザーの情報がオブジェクトに現在選択されている統合開発環境 (IDE) の保持*コンテキスト*します。 選択範囲のコンテキストで Vspackage を活用する通貨の 2 つの方法で追跡。  
  
-   によって、通貨については、IDE に Vspackage を伝達します。  
  
-   IDE 内でユーザーの現在アクティブな選択を監視します。  
  
## <a name="selection-context"></a>選択範囲のコンテキスト  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE グローバルの追跡 IDE の通貨で独自のグローバルの選択コンテキスト オブジェクト。 次の表では、選択コンテキストを構成する要素を示します。  
  
|要素|説明|  
|-------------|-----------------|  
|現在の階層|現在のプロジェクトでは通常;NULL の現在の階層は、ソリューション全体が現在ことを示します。|  
|現在のアイテム Id|現在の階層内で選択した項目project ウィンドウで複数の選択肢がある場合は、複数の現在の項目があります。|  
|現在の `SelectionContainer`|1 つまたは複数のオブジェクトのプロパティ ウィンドウがプロパティを表示する必要がありますを保持します。|  
  
 さらに、環境では、2 つのグローバル リストを保持しています。  
  
-   アクティブな UI コマンド識別子の一覧  
  
-   現在アクティブな要素の型の一覧。  
  
### <a name="window-types-and-selection"></a>ウィンドウの種類と選択  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE では、2 つの一般的な種類に windows が整理されます。  
  
- 階層型の windows  
  
- ツールとドキュメント ウィンドウなどのフレーム ウィンドウ  
  
  IDE は、これらのウィンドウの種類ごとに異なる方法で通貨を追跡します。  
  
  最も一般的なプロジェクトの種類 ウィンドウは、IDE を制御するソリューション エクスプ ローラーです。 プロジェクトの種類 ウィンドウは、グローバルな階層と、グローバルの選択コンテキストの ItemID を追跡し、ウィンドウが現在の階層を決定する、ユーザーの選択に依存しています。 プロジェクトの種類の windows の場合、環境には、グローバル サービスが備わっています<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>を使用して、どの Vspackage が開いている要素の現在の値を監視できます。 プロパティの参照、環境では、このグローバル サービスによって駆動されます。  
  
  フレーム ウィンドウ、その一方で、使用して、DocObject フレーム ウィンドウ内でプッシュ SelectionContext 値 (階層/ItemID/SelectionContainer 忍耐)。 . フレーム ウィンドウは、サービスを使用して<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>この目的のためです。 DocObject は選択コンテナーでは、値のみをプッシュできる階層構造のローカル値のままと通常 MDI 子ドキュメントの ItemID が変更されません。  
  
### <a name="events-and-currency"></a>イベントと通貨  
 通貨の環境の概念に影響する 2 種類のイベントが発生する可能性があります。  
  
-   グローバル レベルに伝達され、ウィンドウ フレームの選択コンテキストを変更するイベントです。 このようなイベントの例には、グローバル ツール ウィンドウが開かれている、または開いているプロジェクトの種類のツール ウィンドウは、開いている MDI 子ウィンドウが含まれます。  
  
-   トレース ウィンドウ フレームの選択コンテキスト内で要素を変更するイベントです。 例には、プロジェクトの種類 ウィンドウで選択を変更するか DocObject 内の選択範囲の変更が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)   
 [ユーザーへのフィードバック](../../extensibility/internals/feedback-to-the-user.md)

