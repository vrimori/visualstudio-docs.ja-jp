---
title: XML コマンド テーブルのデザイン (します。Vsct) ファイル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b72438998b75fcebc7cccae082e3e9db4ac13b69
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537916"
---
# <a name="designing-xml-command-table-vsct-files"></a>XML コマンド テーブルのデザイン (します。Vsct) ファイル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[XML コマンド テーブルの設計 (します。Vsct) ファイル](https://docs.microsoft.com/visualstudio/extensibility/internals/designing-xml-command-table-dot-vsct-files)します。  
  
XML コマンド テーブル (.vsct) ファイルには、VSPackage のコマンドの項目の外観とレイアウトについて説明します。 コマンドの項目には、ボタン、コンボ ボックス、メニューのツールバー、およびコマンドのアイテムのグループが含まれます。 このトピックでは、XML コマンド テーブルのファイル、コマンドの項目、メニューの影響、およびそれらを作成する方法について説明します。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>コマンド、メニューのグループ、および、.vsct ファイル  
 .vsct ファイルは、コマンド、メニューのおよびコマンド グループに編成されます。 .Vsct ファイル内の XML タグの各コマンド ボタン、コマンドの配置、およびビットマップなどの他の関連項目と共に、これらの項目を表します。  
  
 実行して新しい VSPackage を作成する場合、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]パッケージ テンプレートでは、メニュー コマンド、ツール ウィンドウ、または、選択内容に応じて、カスタム エディターに必要な要素の .vsct ファイルが生成されます。 この .vsct ファイルは、特定の VSPackage の要件に合わせて変更できます。 .Vsct ファイルを変更する方法の例については、例を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 新しい、空白の .vsct ファイルを作成するを参照してください。[方法: を作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)します。 作成されると、ファイルに、コマンドの項目のレイアウトを記述する XML 要素、属性、および値を追加します。 詳細な XML スキーマでは、次を参照してください。、 [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)します。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc と .vsct ファイルの間の相違点  
 現在、将来の .ctc ファイル形式が非推奨として、.vsct ファイル内の XML タグの意味は同じですが、その実装は少し異なります。  
  
-   新しい **\<extern >** はタグなど、コンパイルするには、その他の .h ファイルを参照する、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ツールバー。  
  
-   .Vsct ファイルのサポート、 **/include**ステートメントでは、.ctc ファイルと同様、これも新機能が\<**インポート >** 要素。 相違点は、 **/include**は**すべて**の情報が\<**インポート >** 名のみが表示されます。  
  
-   .Ctc ファイルには、プリプロセッサ ディレクティブを定義するヘッダー ファイルが必要ですが、1 つは .vsct ファイルは必要ありません。 代わりにある、シンボル テーブルに、ディレクティブを配置、 **\<シンボル >** .vsct ファイルの下部にある要素。  
  
-   .vsct ファイルの機能、 **\<注釈 >** タグで、メモや図などのような情報を埋め込むことができます。  
  
-   値は、項目の属性として格納されます。  
  
-   コマンドのフラグを個別に格納されているまたは積み上げことができます。  積み上げコマンド フラグでただし、Intellisense は機能しません。 コマンドのフラグの詳細については、次を参照してください。、 [Command Flag 要素](../../extensibility/command-flag-element.md)します。  
  
-   分割のドロップダウン リストから、combos など、複数の種類を指定することができます。  
  
-   Guid は検証はありません。  
  
-   各 UI 要素には、それに表示されるテキストを表す文字列があります。  
  
-   親は省略可能です。 省略した場合は、"グループ Unknown"の値が使用されます。  
  
-   アイコンの引数は省略可能です。  
  
-   ビットマップ セクション--、.ctc と同じファイルが、コンパイル時、vsct.exe コンパイラによってプルされ href を使用してファイル名を指定できるようになりました。  
  
-   ResID--古いビットマップのリソース ID は、ことができ、同じ .ctc ファイルのように動作します。  
  
-   HRef--新しいメソッドをビットマップ リソースのファイル名を指定することができます。 使用のセクションを省略するためすべてを使用すると想定しています。 任意のネットワークの共有にし、ファイルのローカル リソースおよび/I スイッチで定義されるリソース最初に、コンパイラが検索されます。  
  
-   Keybinding--エミュレーターを指定する必要なくなりました。 いずれかを指定して、コンパイラ、エディターと、エミュレーターは、同じであると想定されます。  
  
-   Keychord - が削除されました。 新しい形式では、Key1、Mod1、Key2、Mod2 です。  文字、16 進数、または VK 定数のいずれかを指定することができます。  
  
 新しいコンパイラ、vsct.exe、.ctc と .vsct ファイルをコンパイルします。 古い ctc.exe コンパイラ、ただしは認識も .vsct ファイルをコンパイルします。  
  
 Vsct.exe コンパイラを使用して、.vsct ファイルを既存の .cto ファイルに変換することができます。 詳細については、次を参照してください。[方法: を作成します。既存の Vsct ファイルです。Cto ファイル](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)します。  
  
## <a name="the-vsct-file-elements"></a>.Vsct ファイルの要素  
 コマンド テーブルには、次の階層と要素があります。  
  
 [CommandTable 要素](../../extensibility/commandtable-element.md)-すべてのコマンド、メニュー グループ、および VSPackage に関連付けられているメニューを表します。  
  
 [Extern 要素](../../extensibility/extern-element.md): .vsct ファイルをマージする任意の外部の .h ファイルを参照します。  
  
 [要素を含める](../../extensibility/include-element.md)— your.vsct ファイルと共にコンパイルする任意の追加のヘッダー (.h) ファイルを参照します。 .Vsct ファイルでは、コマンド、メニュー グループ、およびメニュー IDE または別の VSPackage を提供するを定義する定数を含む .h ファイルを含めることができます。  
  
 [要素をコマンド](../../extensibility/commands-element.md)-すべての実行可能な個々 のコマンドを表します。 各コマンドには、次の 4 つの子要素があります。  
  
 [Menus 要素](../../extensibility/menus-element.md)-すべてのメニューとツールバーで、VSPackage を表します。 メニューは、コマンドのグループのコンテナーです。  
  
 [Groups 要素](../../extensibility/groups-element.md)-すべての VSPackage でグループを表します。 グループは、個々 のコマンドのコレクションです。  
  
 [要素をボタン](../../extensibility/buttons-element.md)-すべてのコマンド ボタンと、VSPackage でのメニュー項目を表します。 ボタンは、コマンドに関連付けることができるビジュアル コントロールです。  
  
 [Bitmaps 要素](../../extensibility/bitmaps-element.md)— すべて、VSPackage でボタンのビットマップのすべてを表します。 ビットマップは、または、コンテキストに応じて、コマンド ボタンの横に表示される画像です。  
  
 [CommandPlacements 要素](../../extensibility/commandplacements-element.md)— 個々 のコマンドを VSPackage のメニューに配置する必要があります追加の場所を示します。  
  
 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)— コマンド表示すべての時間、または特定のダイアログ ボックスまたはウィンドウが表示される場合など、特定のコンテキストでのみかどうかを指定します。 メニューとコマンドをこの要素の値を持つ、指定したコンテキストがアクティブな場合にのみが表示されます。 既定の動作では、常に、コマンドが表示されます。  
  
 [KeyBindings 要素](../../extensibility/keybindings-element.md)-コマンドの任意のキー バインドを指定します。 つまり、1 つまたは複数のキーの組み合わせなど、コマンドを実行する押す必要がある**CTRL + S**します。  
  
 [UsedCommands 要素](../../extensibility/usedcommands-element.md)— Informs、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境が、現在の VSPackage がアクティブなときに、その他のコードで指定されたコマンドが実装されていることコマンドの実装を提供します。  
  
 `Symbols Element` — シンボルの名前とすべてのパッケージにコマンドの GUID Id が含まれています。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct ファイルのデザイン ガイドライン  
 .Vsct ファイルを正常に設計するには、次のガイドラインに従います。  
  
-   グループでのみコマンドを配置することができます、メニューのでのみのグループを配置できるおよびメニューは、グループにのみ配置できます。 メニューにのみは実際には、IDE では、グループに表示され、コマンドはできません。  
  
-   サブメニューは、メニューに直接割り当てることはできませんが、メニューにさらに割り当てられているグループに割り当てる必要があります。  
  
-   1 つの親グループまたはその定義のディレクティブの親フィールドを使用してメニュー コマンド、サブメニュー、およびグループを割り当てることができます。  
  
-   ディレクティブは、親フィールドを通じてのみコマンド テーブルを整理すると、重要な制限があります。 オブジェクトを定義するディレクティブでは、1 つだけの親引数を実行できます。  
  
-   独自のオブジェクトの新しいインスタンスを作成する新しいディレクティブの使用を要求するコマンド、グループ、またはサブメニューを再利用`GUID:ID`ペア。  
  
-   各`GUID:ID`ペアは一意である必要があります。 によって処理は、たとえば、配置されたツールバー、メニューまたはコンテキスト メニューで、コマンドを再利用、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。  
  
-   コマンドとサブメニューを複数のグループに割り当ても、グループを使用して複数のメニューに割り当てることができます、[コマンド要素](../../extensibility/commands-element.md)します。  
  
## <a name="vsct-file-notes"></a>.Vsct ファイルのノート  
 実行する必要がありますそれをコンパイルして、ネイティブ サテライト DLL に配置した後に、.vsct ファイルにすべての変更を加えた場合**devenv.exe/setup/nosetupvstemplates**します。 この操作により、VSPackage のリソースを再読み込みするのには、実験用のレジストリと記述されている内部データベースで指定された[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]再構築されます。  
  
 開発時に、複数の VSPackage プロジェクトが作成され、IDE での混乱を招くの煩雑さにつながる可能性がある実験用のレジストリ ハイブに登録されている可能性があります。 これを解決するには、登録されているすべての Vspackage と ide が行った変更を削除する既定の設定に、実験用ハイブをリセットできます。 実験用ハイブをリセットするには、Visual Studio SDK に付属する CreateExpInstance.exe ツールを使用してください。 検索できます。  
  
 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 コマンドラインを使用してツールを実行**CreateExpInstance/Reset**します。 実験用ハイブから削除しますこのツールが、通常にインストールされているすべての登録されている Vspackage を使用することに注意してください。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)

