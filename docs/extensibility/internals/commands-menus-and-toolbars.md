---
title: コマンド、メニューのおよびツールバー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 686e3a5df183d7296aba8eacffbf061d4d5f958f
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510807"
---
# <a name="commands-menus-and-toolbars"></a>コマンド、メニューのおよびツールバー
メニューとツールバーは、ユーザーが、VSPackage のコマンドにアクセスします。 コマンドは、ドキュメントの印刷、ビューの更新、ファイルの新規作成などのタスクを実行する関数です。 メニューとツール バーは、ユーザーにコマンドをグラフィカルに表示する便利な方法です。 通常、関連するコマンドは、同じメニューやツール バーにまとめられます。  
  
-   メニューは通常、統合開発環境 (IDE) やツール ウィンドウの上部にある列にまとめられた 1 語の文字列として表示されます。 メニューは、右クリック イベントの結果として表示することもでき、これはそのコンテキストのショートカット メニューと呼ばれます。 クリックすると、メニューが展開して 1 つ以上のコマンドが表示されます。 コマンドをクリックすると、タスクを実行したり、追加のコマンドを含むサブメニューを起動したりすることができます。 一部のよく知られているメニュー名が**ファイル**、**編集**、**ビュー**、および**ウィンドウ**します。 詳細については、次を参照してください。[メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)します。  
  
-   ツール バーは通常、ボタンと他のコントロール (コンボ ボックス、リスト ボックス、テキスト ボックス、メニュー コント ローラーなど) の行です。 すべてのツール バー コントロールは、コマンドに関連付けられます。 ツール バー ボタンをクリックすると、関連付けられているコマンドがアクティブ化されます。 ツール バー ボタンには、通常、[印刷] コマンド用のプリンターなどの基になるコマンドを示すアイコンがあります。 ドロップダウン リスト コントロールでは、リスト内の各項目は、異なるコマンドに関連付けられています。 メニュー コントローラーは、コントロールの一方の側がツール バー ボタン、もう一方の側が、クリックして追加のコマンドを表示する下矢印の組み合わせです。 詳細については、次を参照してください。[ツールバーにメニュー コント ローラーを追加](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)します。  
  
-   コマンドを作成するときは、コマンド用のイベント ハンドラーも作成する必要があります。 イベント ハンドラーでは、コマンドをいつ表示または有効にするかを決定し、コマンドのテキストを変更し、アクティブ化したときにコマンドが適切に応答する (「ルーティングする」) ようにすることができます。 ほとんどの場合、IDE の処理コマンドを使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。 コマンドを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]最も内側のコマンド コンテキスト、ローカルの選択に基づくし、グローバルの選択に基づいて、最も外側のコンテキストに進みます以降、階層的にルーティングします。 メイン メニューに追加したコマンドは、すぐにスクリプトに利用できます。 詳細については、次を参照してください。 [Menucommand とします。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)と[コンテキスト オブジェクトの選択](../../extensibility/internals/selection-context-objects.md)します。  
  
 新しいメニューおよびツールバーを定義する必要がありますで記述したそれらを Visual Studio コマンド テーブル (*.vsct*) ファイル。 Visual Studio パッケージ テンプレートは、どのようなコマンド、ツールバー、およびテンプレートの選択されているエディターをサポートするために必要な要素と共に、このファイルを作成します。 または、書き込める独自 *.vsct*ファイルをここで説明されている XML スキーマを使用して: [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)します。  
  
 操作の詳細については *.vsct*ファイルを参照してください[Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
 このセクションのトピックでは、Vspackage でのコマンド、メニューのおよびツールバーのしくみについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 コマンド テーブルの書式指定の詳細な説明。  
  
 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 XML ベースの構文およびコマンド テーブル コンパイラについて説明します。  
  
 [既定のコマンド、グループ、およびツールバーの配置](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 定義済みのコマンド、グループ、メニューのおよびツールバーについて説明します。  
  
 [IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 定義済みのメニューのコマンド、およびコマンド グループで使用できるように指定します、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 [コマンド デザイン](../../extensibility/internals/command-design.md)  
 コマンドを設計する方法について説明します。  
  
 [メニューとツールバーのコマンドを最適化します。](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 コマンドについてのガイドラインを提供します。  
  
 [コマンドを使用可能します。](../../extensibility/internals/making-commands-available.md)  
 Visual Studio でのコマンドを使用できるようにする方法について説明します。  
  
 [相互運用機能アセンブリを使用するコマンドとメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 相互運用機能アセンブリを使用するコマンドを実装する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)  
 Vspackage でのコマンド ルーティングについて説明します。