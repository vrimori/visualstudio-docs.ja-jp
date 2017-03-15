---
title: "XML コマンド テーブルの設計 (します。Vsct) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>XML コマンド テーブルの設計 (します。Vsct) ファイル
XML コマンド テーブル (.vsct) ファイルは、VSPackage のコマンドのアイテムの外観とレイアウトを説明します。 コマンドの項目には、ボタン、コンボ ボックス、メニューのツールバー、およびコマンドのアイテムのグループが含まれます。 このトピックでは、XML コマンド テーブルのファイル、コマンド項目、メニューの影響、およびその作成方法について説明します。  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>コマンド、メニューのグループ、および .vsct ファイル  
 .vsct ファイルは、コマンド、メニューのおよびコマンド グループの周囲にまとめられます。 .Vsct ファイル内の XML タグでは、各コマンド ボタン、コマンドの配置、およびビットマップなどの関連するその他の項目と共に、これらの項目を表します。  
  
 実行して、新しい VSPackage を作成する場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージ テンプレート、メニュー コマンド、ツール ウィンドウで、または選択に応じて、カスタム エディターの必要な要素を持つ .vsct ファイルが生成されます。 この .vsct ファイルは、固有の VSPackage の要件に合わせて変更できます。 .Vsct ファイルを変更する方法の例については、例を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
 新しい、空白の .vsct ファイルを作成するを参照してください。[する方法: 作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)します。 作成されると、ファイルに、コマンドの項目のレイアウトを記述する XML 要素、属性、および値を追加します。 詳細な XML スキーマを参照してください、 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)します。  
  
## <a name="differences-between-ctc-and-vsct-files"></a>.Ctc .vsct ファイル間の相違点  
 .Vsct ファイル内の XML タグの意味は同じ .ctc ファイル形式は、現在の非推奨が、その実装は少し異なります。  
  
-   新しい** \<extern >**はタグなど、コンパイルするには、その他の .h ファイルを参照する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ツールバーです。  
  
-   .Vsct ファイルのサポート、 **/include**ステートメント、.ctc ファイルのように、これも新機能が\<**インポート >**要素。 点が異なります**/include**に取り込まれる**すべて**、情報が、 \<**インポート >**名前のみで表示します。  
  
-   .Ctc ファイルには、プリプロセッサ ディレクティブを定義するヘッダー ファイルが必要とする、.vsct ファイルの必要があります。 代わりにある、シンボル テーブルに、ディレクティブを配置、 **\<シンボル >** .vsct ファイルの下部にある要素。  
  
-   .vsct ファイルの機能、 **\<注釈 >**タグで、メモまたは画像もなど、必要なすべての情報を埋め込むことができます。  
  
-   値は、項目の属性として保存されます。  
  
-   コマンドのフラグは、個別に格納されているまたは積み上げできます。  Intellisense、ただしでは動作しません積み上げコマンド フラグ。 コマンドのフラグの詳細については、次を参照してください。、[コマンド フラグ要素](../../extensibility/command-flag-element.md)します。  
  
-   分割のドロップダウン リストから、コンボなどの複数の種類を指定できます。  
  
-   Guid は検証されません。  
  
-   各 UI 要素には、それに表示されるテキストを表す文字列があります。  
  
-   親はオプションです。 省略すると、「グループ不明」の値が使用されます。  
  
-   アイコンの引数は省略できます。  
  
-   ビットマップのセクションに、.ctc と同じ - ファイルが取り込まれる vsct.exe コンパイラによってコンパイル時に href を使用してファイル名を指定できるようになりました。  
  
-   ResID--古いビットマップ リソース ID は使用でき、.ctc ファイルでも同じです。  
  
-   HRef--ビットマップ リソースのファイル名を指定することができます新しいメソッドです。 使用済みのセクションを省略すると、すべてを使用するものです。 任意のネットワーク共有上のファイルのローカル リソースおよび/I スイッチによって定義されているリソースは、まず、コンパイラが検索されます。  
  
-   Keybinding--エミュレーターを指定する必要不要になった。 を指定したいずれかの場合、コンパイラはエディターとエミュレーターは、同じであると仮定します。  
  
-   Keychord--が削除されました。 新しい形式は、Key1、Mod1、Key2、Mod2 です。  文字、16 進数、または VK 定数のいずれかを指定することができます。  
  
 新しいコンパイラ、vsct.exe、.ctc と .vsct の両方のファイルをコンパイルします。 旧バージョンの ctc.exe コンパイラただしは認識も .vsct ファイルをコンパイルします。  
  
 Vsct.exe コンパイラを使用すると、既存の .cto ファイルを .vsct ファイルに変換します。 詳細については、次を参照してください。[方法: 作成、します。既存の Vsct ファイルです。最高技術責任者ファイル](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)します。  
  
## <a name="the-vsct-file-elements"></a>.Vsct ファイルの要素  
 コマンド テーブルには、次のような階層および要素があります。  
  
 [CommandTable 要素](../../extensibility/commandtable-element.md)-すべての VSPackage に関連付けられているメニューのコマンド、およびメニュー グループを表します。  
  
 [Extern 要素](../../extensibility/extern-element.md)— .vsct ファイルを使用してマージする任意の外部の .h ファイルを参照します。  
  
 [要素を含める](../../extensibility/include-element.md)— your.vsct ファイルと共にコンパイルする任意の追加のヘッダー (.h) ファイルを参照します。 .Vsct ファイルには、コマンド、メニュー グループ、およびメニュー IDE または別の VSPackage を提供するを定義する定数を含む .h ファイルを含めることができます。  
  
 [要素をコマンド](../../extensibility/commands-element.md)-すべてを実行する個々 のコマンドを表します。 各コマンドには、次の&4; つの子要素があります。  
  
 [メニュー要素](../../extensibility/menus-element.md)-すべてのメニューとツールバー、VSPackage で表します。 メニューは、コマンドのグループのコンテナーです。  
  
 [Groups 要素](../../extensibility/groups-element.md)-すべての VSPackage でグループを表します。 グループは、個々 のコマンドのコレクションです。  
  
 [要素をボタン](../../extensibility/buttons-element.md)-すべてのコマンド ボタンに、VSPackage でのメニュー項目を表します。 ボタンは、コマンドに関連付けることができるビジュアル コントロールです。  
  
 [ビットマップ要素](../../extensibility/bitmaps-element.md)-すべての VSPackage でボタン用のビットマップのすべてを表します。 ビットマップは、または、状況に応じて、コマンド ボタンの横に表示される画像です。  
  
 [CommandPlacements 要素](../../extensibility/commandplacements-element.md)— 個々 のコマンドを VSPackage のメニューに配置する必要があります別の場所を示します。  
  
 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)— コマンド表示まったく回、または特定のダイアログ ボックスまたはウィンドウが表示される場合など、特定のコンテキストでのみかどうかを指定します。 メニューとこの要素の値を持つコマンドは、指定したコンテキストがアクティブな場合にのみ表示されます。 既定の動作では、常に、コマンドが表示されます。  
  
 [ショートカット キー要素](../../extensibility/keybindings-element.md)— コマンドは、すべてのキー バインドを指定します。 つまり、1 つまたは複数のキーの組み合わせを押すことによりなど、コマンドを実行する必要があります**CTRL + S**します。  
  
 [UsedCommands 要素](../../extensibility/usedcommands-element.md)— Informs、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境が、現在 VSPackage がアクティブなときに、その他のコードで指定されたコマンドが実装されていることコマンドの実装を提供します。  
  
 `Symbols Element`-記号名、すべてのパッケージのコマンド用の Id を GUID が含まれています。  
  
## <a name="vsct-file-design-guidelines"></a>.Vsct ファイルのデザイン ガイドライン  
 .Vsct ファイルをデザインするには、これらのガイドラインに従ってください。  
  
-   コマンドは、グループにのみ配置できる、グループは、メニューにのみ配置できるおよびメニューは、グループにのみ配置できます。 IDE では、グループ メニューにのみが表示される実際には、コマンドなっています。  
  
-   サブメニューは、メニューに直接割り当てることはできませんが、メニューには、さらに割り当てられているグループに割り当てる必要があります。  
  
-   1 つの親グループまたはその定義のディレクティブの親フィールドを使用してメニューには、コマンド、サブメニュー、およびグループを割り当てることができます。  
  
-   ディレクティブ内の親フィールドを通じてのみコマンド テーブルを整理すると、重要な制限があります。 オブジェクトを定義するディレクティブでは、1 つだけの親の引数を受け取ります。  
  
-   コマンド、グループ、またはサブメニューを再利用するには、独自のオブジェクトの新しいインスタンスを作成する新しいディレクティブの使用が必要です。`GUID:ID`ペア。  
  
-   各`GUID:ID`の組は一意である必要があります。 によって処理は、たとえば、配置されたメニューのツールバー、またはコンテキスト メニューで、コマンドを再利用、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイス</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
-   コマンドとサブメニューも、複数のグループに割り当てるでき、複数のメニューを使用するグループを割り当てることが、 [Commands 要素](../../extensibility/commands-element.md)します。  
  
## <a name="vsct-file-notes"></a>.Vsct ファイルに関する注意事項します。  
 実行する必要があります両方コンパイルしてネイティブのサテライト DLL に配置した後に、.vsct ファイルに変更を加えた場合**devenv.exe/setup/nosetupvstemplates**します。 この操作により、実験用にレジストリを再読み込みして記述されている内部データベースに指定される VSPackage リソース[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]に再構築されます。  
  
 開発時に、複数の VSPackage プロジェクトを作成して、IDE の煩雑さを混乱を招く可能性のある実験用のレジストリ ハイブに登録されている可能性があります。 これを解決するには、登録されているすべての VSPackages および IDE に、行った変更を削除する既定の設定に、実験用ハイブをリセットできます。 実験用ハイブをリセットするには、Visual Studio SDK に付属している CreateExpInstance.exe ツールを使用します。 検索できます。  
  
 **% %PROGRAMFILES% (x86) %\Visual Studio\<バージョン > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 コマンドラインを使用してツールを実行**CreateExpInstance/Reset**します。 このツールから削除する、実験用ハイブでは、通常インストールされているすべての登録済み VSPackages に注意してください[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)
