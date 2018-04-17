---
title: XML コマンド テーブルのデザイン (です。Vsct) ファイル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 865baa3f7b4b0fe4cbbaf2cdf34e9e8041d5c121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="designing-xml-command-table-vsct-files"></a>XML コマンド テーブルのデザイン (です。Vsct) ファイル
XML コマンド テーブル (.vsct) ファイルは、VSPackage のコマンドのアイテムの外観とレイアウトを説明します。 コマンドの項目には、ボタン、コンボ ボックス、メニューのツールバー、およびコマンドのアイテムのグループが含まれます。 このトピックでは、XML コマンド テーブルのファイルへの影響についてコマンド項目、メニューのおよびそれらを作成する方法について説明します。

## <a name="commands-menus-groups-and-the-vsct-file"></a>コマンド、メニューのグループ、および、.vsct ファイル
 コマンド、メニューのおよびコマンド グループの周囲は、.vsct ファイルが編成されます。 .Vsct ファイル内の XML タグには、各コマンド ボタン、コマンドの配置、およびビットマップなどの関連するその他の項目と共に、これらの項目を表します。

 実行して、新しい VSPackage を作成する場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージ テンプレートでは、メニュー コマンド、ツール ウィンドウ、または、選択内容に基づいて、カスタム エディターの必要な要素を持つ .vsct ファイルが生成されます。 この .vsct ファイルは、特定の VSPackage の要件を満たすため、変更できます。 例については、.vsct ファイルを変更する方法の例では、[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)です。

 新しい、空白の .vsct ファイルを作成するを参照してください。[する方法: を作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)です。 作成されると、ファイルに、コマンドの項目のレイアウトを記述する XML 要素、属性、および値を追加します。 詳細な XML スキーマでは、次を参照してください。、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)です。

## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc および .vsct ファイル間の相違点
 .Vsct ファイル内の XML タグの意味は、.ctc ファイル形式を現在の非推奨と同じですが、その実装がわずかに異なります。

-   新しい **\<extern >**はタグなどの場合、コンパイルするのには、その他の .h ファイルを参照する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ツールバー。

-   .Vsct ファイルをサポートしている間、 **/include**ステートメントでは、.ctc ファイルと機能も、新しい\<**インポート >**要素。 点が異なります**/include**でによってもたらさ**すべて**、情報が\<**インポート >**名前のみで表示します。

-   .Ctc ファイルには、プリプロセッサ ディレクティブを定義するヘッダー ファイルが必要とする、.vsct ファイルの必要があります。 代わりにある、シンボル テーブルに、ディレクティブを配置、 **\<シンボル >** .vsct ファイルの下部にある要素。

-   .vsct ファイルの機能、 **\<注釈 >**タグで、メモや画像もなどのような情報を埋め込むことができます。

-   値は、項目の属性として保存されます。

-   コマンド フラグを個別に格納されているまたは積み上げことができます。  IntelliSense、ただしは機能しません積み上げコマンド フラグ。 コマンドのフラグの詳細については、次を参照してください。、[コマンド フラグ要素](../../extensibility/command-flag-element.md)です。

-   分割のドロップダウン リスト、コンボなど、複数の種類を指定できます。

-   Guid を検証しません。

-   各 UI 要素には、それに表示されるテキストを表す文字列があります。

-   親は省略可能です。 省略した場合、"グループ Unknown"の値が使用されます。

-   アイコンの引数は省略できます。

-   ビットマップ セクション--、.ctc と同じファイルが、コンパイル時、vsct.exe コンパイラによってプルされ href を使用してファイル名を指定できるようになりました。

-   ResID--古いビットマップ リソース ID と指定できますが、同じ .ctc ファイルと同様に正常に動作します。

-   HRef--新しいメソッドをビットマップ リソースのファイル名を指定することができます。 想定すべてを使用するために使用されるセクションを省略することができます。 ファイルは、ネットワーク共有にし、ローカル リソースおよび/I スイッチによって定義されるリソース最初、コンパイラが検索されます。

-   Keybinding--エミュレーターを指定する必要不要になった。 を指定したいずれかの場合、コンパイラはエディターと、エミュレーターは、同じであると仮定します。

-   Keychord--は削除されました。 新しい形式は、Key1、Mod1、Key2、Mod2 です。  文字、16 進数、または VK 定数のいずれかを指定することができます。

 新しいコンパイラ、vsct.exe、.ctc および .vsct ファイルの両方をコンパイルします。 古い ctc.exe コンパイラ、ただしは認識も .vsct ファイルをコンパイルします。

 Vsct.exe コンパイラを使用して、.vsct ファイルに既存の .cto ファイルを変換することができます。 詳細については、次を参照してください。[する方法: 作成、します。既存の Vsct ファイルです。Cto ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)です。

## <a name="the-vsct-file-elements"></a>.Vsct ファイルの要素
 コマンド テーブルは、次の階層および要素があります。

 [CommandTable 要素](../../extensibility/commandtable-element.md)— すべての VSPackage に関連付けられたメニューのコマンド、およびメニュー グループを表します。

 [Extern 要素](../../extensibility/extern-element.md)— .vsct ファイルとマージする任意の外部の .h ファイルを参照します。

 [要素を含める](../../extensibility/include-element.md)— your.vsct ファイルと共にコンパイルする追加のヘッダー (.h) ファイルを参照します。 .Vsct ファイルでは、コマンド、メニュー グループ、およびメニュー IDE または別の VSPackage を提供するを定義する定数を含む .h ファイルを含めることができます。

 [要素をコマンド](../../extensibility/commands-element.md)— すべての実行可能な個別のコマンドを表します。 各コマンドには、次の 4 個の子要素があります。

 [メニュー要素](../../extensibility/menus-element.md)— すべてのメニューとツールバー、VSPackage で表します。 メニューは、コマンドのグループのコンテナーです。

 [Groups 要素](../../extensibility/groups-element.md)— すべての VSPackage でグループを表します。 グループは、個々 のコマンドのコレクションです。

 [要素の各ボタン](../../extensibility/buttons-element.md)— すべてのコマンド ボタンと、VSPackage でのメニュー項目を表します。 ボタンは、コマンドと関連付けることができるビジュアル コントロールです。

 [ビットマップ要素](../../extensibility/bitmaps-element.md)— すべての VSPackage のボタンのすべてのビットマップを表します。 ビットマップは、または、コンテキストに応じて、コマンド ボタンの横に表示される画像です。

 [CommandPlacements 要素](../../extensibility/commandplacements-element.md)— 個々 のコマンドを VSPackage のメニューに配置する必要があります別の場所を示します。

 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)— コマンド表示すべての時刻、または特定のダイアログ ボックスまたはウィンドウが表示される場合など、特定のコンテキストでのみかどうかを指定します。 メニューと、この要素の値を持つコマンドが指定されたコンテキストがアクティブな場合にのみ表示されます。 既定の動作では、常に、コマンドが表示されます。

 [KeyBindings 要素](../../extensibility/keybindings-element.md)— コマンドに対する任意のキー バインドを指定します。 つまり、1 つまたは複数のキーの組み合わせなど、コマンドの実行に押す必要がある**CTRL + S**です。

 [UsedCommands 要素](../../extensibility/usedcommands-element.md)— Informs、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境が、指定されたコマンドは、その他のコードで実装されている、現在の VSPackage がアクティブなとき、いるコマンドの実装を提供します。

 `Symbols Element` -記号名、すべてのパッケージのコマンド用の Id を GUID が含まれています。

## <a name="vsct-file-design-guidelines"></a>.Vsct ファイルのデザイン ガイドライン
 .Vsct ファイルを正常に設計するには、次のガイドラインに従います。

-   コマンドは、グループでのみ配置することができます、メニューのでのみのグループを配置できるおよびメニューは、グループにのみ配置できます。 IDE では、グループ メニューにのみが表示される実際には、コマンドはできません。

-   サブメニューでは、メニューに直接割り当てることができませんが、メニューにさらに割り当てられているグループに割り当てる必要があります。

-   1 つの親グループまたはその定義のディレクティブの親フィールドを使用してメニューには、コマンド、サブメニュー、およびグループを割り当てることができます。

-   ディレクティブは、親フィールドを通じてのみコマンド テーブルを整理すると、重要な制限があります。 オブジェクトを定義するディレクティブでは、1 つだけの親引数を受け取ることができます。

-   独自のオブジェクトの新しいインスタンスを作成する新しいディレクティブの使用を要求するコマンド、グループ、またはサブメニューを再利用して`GUID:ID`ペア。

-   各`GUID:ID`ペアは一意である必要があります。 によって処理は、たとえば、配置されたメニュー、ツールバー、またはコンテキスト メニューで、コマンドを再利用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスです。

-   コマンドとサブメニューのも、複数のグループに割り当てるでき、グループを使用して複数のメニューに割り当てることができます、[コマンド要素](../../extensibility/commands-element.md)です。

## <a name="vsct-file-notes"></a>.Vsct ファイルの注意事項
 実行する必要があります両方指定してコンパイルしてネイティブ サテライト DLL に配置することに、.vsct ファイルにすべての変更を加えた場合**devenv.exe/setup/nosetupvstemplates**です。 この操作により、再読み込みするのには、実験用のレジストリと記述されている内部データベースで指定されたリソースに VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]再構築されます。

 開発時に、複数の VSPackage プロジェクトを作成しても、IDE での混乱を招く乱雑につながる可能性がある実験用レジストリ ハイブに登録されている可能性があります。 これを解決するには、登録されているすべての VSPackages および IDE に、行った変更を削除する既定の設定に、実験用ハイブをリセットできます。 実験用ハイブをリセットするには、Visual Studio SDK に付属している CreateExpInstance.exe ツールを使用します。 これを見つけることができます。

 **%PROGRAMFILES(x86)%\Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**

 コマンドラインを使用してツールを実行**CreateExpInstance/Reset**です。 このツールから削除する、実験用ハイブでは、通常インストールされているすべての登録済み Vspackage に注意してください[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。

## <a name="see-also"></a>関連項目
 [メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)