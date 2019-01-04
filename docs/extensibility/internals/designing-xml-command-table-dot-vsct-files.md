---
title: XML コマンド テーブルのデザイン (します。Vsct) ファイル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eacbe69488d605d9cde2fb219a8adbca1419361b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904297"
---
# <a name="design-xml-command-table-vsct-files"></a>XML コマンド テーブル (.vsct) ファイルを設計します。
XML コマンド テーブル (*.vsct*) ファイルは、VSPackage のコマンドの項目の外観とレイアウトについて説明します。 コマンドの項目には、ボタン、コンボ ボックス、メニューのツールバー、およびコマンドのアイテムのグループが含まれます。 この記事では、XML コマンド テーブルのファイル、コマンドの項目、メニューの影響、およびそれらを作成する方法について説明します。

## <a name="commands-menus-groups-and-the-vsct-file"></a>コマンド、メニューのグループ、および、.vsct ファイル
 *.Vsct*コマンド、メニューのおよびコマンド グループに関連ファイルを編成します。 内に XML タグ、 *.vsct*ファイル コマンド ボタン、コマンドの配置、およびビットマップなどの他の関連項目と共に、これらの各項目を表します。

 実行して新しい VSPackage を作成する場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージのテンプレートがテンプレートによって生成、 *.vsct*メニュー コマンド、ツール ウィンドウ、または、選択内容に応じて、カスタム エディターの必要な要素を持つファイル。 これは、 *.vsct*ファイルは、特定の VSPackage の要件を満たす、変更できます。 変更する方法の例については、 *.vsct*ファイルを参照してください[メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)します。

 新しいを作成するには、空白 *.vsct*ファイルを参照してください[方法。作成、 *.vsct*ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)します。 作成されると、ファイルに、コマンドの項目のレイアウトを記述する XML 要素、属性、および値を追加します。 詳細な XML スキーマでは、次を参照してください。、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)します。

## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc と .vsct ファイルの間の相違点
 XML の背後にある意味でタグの中に、 *.vsct*ファイルは、現在は非推奨では、そのタグと同じ *.ctc*ファイル形式では、その実装は少し異なります。

- 新しい **\<extern >** タグは、その他を参照している *.h*などそれらのファイルをコンパイルするファイル、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ツールバー。

- 中に *.vsct*ファイルのサポート、 **/include**ステートメントとして *.ctc*ファイルは、新しい機能も**\<インポート >** 要素。 相違点は、 **/include**は*すべて*、情報の中に**\<インポート >** 名のみが表示されます。

- 中に *.ctc*ファイルには、プリプロセッサ ディレクティブを定義するヘッダー ファイルが必要な 1 つは必要ありません *.vsct*ファイル。 代わりにある、シンボル テーブルに、ディレクティブを配置、 **\<シンボル >** の下部にある要素、 *.vsct*ファイル。

- *.vsct*ファイル機能、 **\<注釈 >** タグで、メモや図などのような情報を埋め込むことができます。

- 値は、項目の属性として格納されます。

- コマンドのフラグを個別に格納されているまたは積み上げことができます。  積み上げコマンド フラグでただし、IntelliSense は機能しません。 コマンドのフラグの詳細については、次を参照してください。、 [CommandFlag 要素](../../extensibility/command-flag-element.md)します。

- 分割のドロップダウン リストから、combos など、複数の種類を指定することができます。

- Guid は検証はありません。

- 各 UI 要素には、それに表示されるテキストを表す文字列があります。

- 親は省略可能です。 省略した場合、値*グループ不明な*使用されます。

- *アイコン*引数は省略可能です。

- ビットマップのセクション:このセクションと同様、 *.ctc*によって取り込ま Href を使用してファイル名を指定できるようになりましたことを除いて、ファイル、 *vsct.exe*コンパイラがコンパイル時にします。

- ResID:古いビットマップ リソースの ID には、使用、および静止の動作と同じ *.ctc*ファイル。

- HRef。新しいメソッドをビットマップ リソースのファイル名を指定することができます。 使用のセクションを省略するためすべてを使用すると想定しています。 ローカル リソース ファイルは、すべてのネットワークの共有をコンパイラが検索最初およびによって定義されているすべてのリソース、 **/I**スイッチします。

- キー バインド:エミュレーターを指定する必要がなくなりました。 いずれかを指定して、コンパイラ、エディターと、エミュレーターは、同じであると想定されます。

- Keychord:Keychord が削除されました。 新しい形式は *、Key1、Mod1、Key2 Mod2*します。  文字、16 進数、または VK 定数のいずれかを指定することができます。
       
新しいコンパイラで*vsct.exe*、両方のコンパイル *.ctc*と *.vsct*ファイル。 古い*ctc.exe*ただし、コンパイラが認識またはコンパイル *.vsct*ファイル。

使用することができます、 *vsct.exe*既存を変換するコンパイラ *.cto*ファイルを *.vsct*ファイル。 詳細については、「[方法 :既存の .cto ファイルから .vsct ファイルを作成](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)です。

## <a name="the-vsct-file-elements"></a>.Vsct ファイルの要素
 コマンド テーブルには、次の階層と要素があります。

 [CommandTable 要素](../../extensibility/commandtable-element.md):すべてのコマンド、メニュー グループ、および VSPackage に関連付けられているメニューを表します。

 [Extern 要素](../../extensibility/extern-element.md):マージする任意の外部の .h ファイルを参照、 *.vsct*ファイル。

 [要素を含める](../../extensibility/include-element.md):参照と共にコンパイルする追加のヘッダー (.h) ファイル、 *.vsct*ファイル。 A *.vsct*ファイルを含めることができます *.h*コマンド、メニュー グループ、およびメニュー IDE または別の VSPackage を提供するを定義する定数を含むファイル。

 [Commands 要素](../../extensibility/commands-element.md):すべての実行可能な個々 のコマンドを表します。 各コマンドには、次の 4 つの子要素があります。

 [Menus 要素](../../extensibility/menus-element.md):すべてのメニューとツールバー、VSPackage で表します。 メニューは、コマンドのグループのコンテナーです。

 [Groups 要素](../../extensibility/groups-element.md):すべての VSPackage でグループを表します。 グループは、個々 のコマンドのコレクションです。

 [Buttons 要素](../../extensibility/buttons-element.md):すべてのコマンド ボタンと、VSPackage でのメニュー項目を表します。 ボタンは、コマンドに関連付けることができるビジュアル コントロールです。

 [Bitmaps 要素](../../extensibility/bitmaps-element.md):VSPackage で、ボタンのすべてのビットマップのすべてを表します。 ビットマップは、または、コンテキストに応じて、コマンド ボタンの横に表示される画像です。

 [CommandPlacements 要素](../../extensibility/commandplacements-element.md):個々 のコマンドを VSPackage のメニューに配置する必要があります、その他の場所を示します。

 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md):時間、または特定のダイアログ ボックスまたはウィンドウが表示される場合など、特定のコンテキストでのみコマンドがまったく表示かどうかを指定します。 メニューとコマンドをこの要素の値を持つ、指定したコンテキストがアクティブな場合にのみが表示されます。 既定の動作では、常に、コマンドが表示されます。

 [KeyBindings 要素](../../extensibility/keybindings-element.md):コマンドの任意のキー バインドを指定します。 つまり、1 つまたは複数のキーの組み合わせなど、コマンドを実行する押す必要がある**Ctrl**+**S**します。

 [UsedCommands 要素](../../extensibility/usedcommands-element.md):通知、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境が、現在の VSPackage がアクティブなときに、その他のコードで指定されたコマンドが実装されていることコマンドの実装を提供します。

 [Symbols 要素](../../extensibility/symbols-element.md):シンボルの名前とすべてのパッケージにコマンドの GUID Id が含まれています。

## <a name="vsct-file-design-guidelines"></a>.vsct ファイルのデザイン ガイドライン
 正常に設計、 *.vsct*ファイルで、これらのガイドラインに従ってください。

-   グループでのみコマンドを配置することができます、メニューのでのみのグループを配置できるおよびメニューは、グループにのみ配置できます。 メニューにのみは実際には、IDE では、グループに表示され、コマンドはできません。

-   サブメニューは、メニューに直接割り当てることはできませんが、メニューにさらに割り当てられているグループに割り当てる必要があります。

-   1 つの親グループまたはその定義のディレクティブの親フィールドを使用してメニュー コマンド、サブメニュー、およびグループを割り当てることができます。

-   ディレクティブは、親フィールドを通じてのみコマンド テーブルを整理すると、重要な制限があります。 オブジェクトを定義するディレクティブでは、1 つだけの親引数を実行できます。

-   独自のオブジェクトの新しいインスタンスを作成する新しいディレクティブの使用を要求するコマンド、グループ、またはサブメニューを再利用`GUID:ID`ペア。

-   各`GUID:ID`ペアは一意である必要があります。 によって処理は、たとえば、配置されたツールバー、メニューまたはコンテキスト メニューで、コマンドを再利用、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス。

-   コマンドとサブメニューを複数のグループに割り当ても、グループを使用して複数のメニューに割り当てることができます、[コマンド要素](../../extensibility/commands-element.md)します。

## <a name="vsct-file-notes"></a>.vsct ファイルのノート
 変更を加えた場合、 *.vsct*ファイルした後でそれをコンパイルして、ネイティブのサテライト DLL に配置、 **devenv.exe/setup/nosetupvstemplates**します。 強制的に再読み込みするのには、実験用のレジストリと記述されている内部データベースに指定される VSPackage のリソースを行う[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]再構築されます。

 開発時に、複数の VSPackage プロジェクトが作成され、IDE での混乱を招くの煩雑さにつながる可能性がある実験用のレジストリ ハイブに登録されている可能性があります。 これを解決するには、登録されているすべての Vspackage と ide が行った変更を削除する既定の設定に、実験用ハイブをリセットできます。 実験用ハイブをリセットするには、Visual Studio SDK に付属する CreateExpInstance.exe ツールを使用してください。 あることにあります。

 *% %PROGRAMFILES (x86) %\Visual Studio\\\<バージョン > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 コマンドを使用してツールを実行**CreateExpInstance/Reset**します。 実験用ハイブから削除しますこのツールが、通常にインストールされているすべての登録されている Vspackage を使用することに注意してください。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。

## <a name="see-also"></a>関連項目
 [メニューとコマンドを拡張します。](../../extensibility/extending-menus-and-commands.md)