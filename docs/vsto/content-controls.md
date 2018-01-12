---
title: "コンテンツ コントロール |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e06075c0e748aab34c4a1df425f95592856217db
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="content-controls"></a>コンテンツ コントロール
  コンテンツ コントロールは、次のような機能を備える文書やテンプレートをデザインするときに使用します。  
  
-   フォームのような、入力を制御するユーザー インターフェイス (UI)。  
  
-   文書やテンプレートの保護されたセクションをユーザーが編集できないように制限する機能。 詳細については、次を参照してください。[文書パーツの保護コンテンツ コントロールを使用して](#Protection)です。  
  
-   データ ソースへのデータ バインディング。 詳細については、次を参照してください。[コンテンツ コントロールへのデータ バインディング](#DataBinding)です。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [Word 2007 コンテンツ コントロールを使用して Visual Studio Tools for the Office System (3.0) へのデータ バインディング](http://go.microsoft.com/fwlink/?LinkId=136785)です。  
  
## <a name="overview-of-content-controls"></a>コンテンツ コントロールの概要  
 コンテンツ コントロールは、ユーザーによる入力および印刷に最適化された UI を備えています。 文書に追加するコンテンツ コントロールには、境界線、タイトル、およびユーザーに情報を提供するための仮テキストを設定できます。 コントロールの境界線とタイトルは、文書を印刷したときには表示されません。  
  
 たとえば、ユーザーが文書のセクションに日付を入力する必要がある場合は、文書に日付選択コントロールを追加できます。 ユーザーがコントロールをクリックすると、日付選択の標準的な UI が表示されます。 コントロールのプロパティを設定して、表示する地域別カレンダーを設定したり、日付形式を指定したりすることもできます。 ユーザーが日付を選択すると、コントロールの UI は非表示になります。ユーザーが文書を印刷すると、日付だけが示されます。  
  
 コンテンツ コントロールは、次のような処理を実行する場合にも役立ちます。  
  
-   ユーザーが文書の一部を編集または削除できないようにする。 これは、文書またはテンプレート内にユーザーが表示できても編集できないようにする必要がある情報が含まれる場合や、ユーザーがコンテンツ コントロールを編集できても削除できないようにしたい場合に役立ちます。  
  
-   文書またはテンプレートの一部をデータにバインドする。 コンテンツ コントロールは、データベース フィールド、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] 内のマネージ オブジェクト、文書に格納されている XML 要素、およびその他のデータ ソースにバインドできます。  
  
 ドキュメントレベルのプロジェクトでは、デザイン時または実行時に、文書にコンテンツ コントロールを追加できます。 VSTO アドイン プロジェクトでは、実行時に任意の開いているドキュメントにコンテンツ コントロールを追加できます。 詳細については、次を参照してください。[する方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)です。  
  
> [!NOTE]  
>  コンテンツ コントロールは、Open XML 形式で保存された文書でのみ使用できます。 Word 97-2003 文書 (.doc) 形式で保存された文書では、コンテンツ コントロールは使用できません。  
  
## <a name="types-of-content-controls"></a>コンテンツ コントロールの種類  
 文書に追加できるコンテンツ コントロールは 9 種類あります。 ほとんどのコンテンツ コントロールには、<xref:Microsoft.Office.Tools.Word> 名前空間内に対応する型が存在します。 また、使用可能なものであればどのようなコンテンツ コントロールになることもできる汎用コントロール、<xref:Microsoft.Office.Tools.Word.ContentControl> を使用することもできます。 利用できるコンテンツ コントロールの各を使用する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: コントロールによるテンプレートを使用してコンテンツを作成する](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)です。  
  
### <a name="building-block-gallery"></a>文書パーツ ギャラリー  
 文書パーツ ギャラリーには、ユーザーの一覧から選択ができるように*ドキュメントのビルド ブロック*ドキュメントに挿入します。 文書パーツは、コンテンツとして何度も使用できるように作成された部品のようなもの (共通の表紙、書式設定された表、ヘッダーなど) です。 詳細については、<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> 型を参照してください。 文書パーツの詳細については、次を参照してください。 [Word 2007 での開発者向けの新](http://msdn.microsoft.com/en-us/74aa6688-65b3-4167-997d-131f26ad8f84)です。  
  
### <a name="check-box"></a>チェック ボックス  
 チェック ボックスは、2 値 (オンまたはオフ) の状態を表す UI です。  
  
 他の種類のコンテンツ コントロールとは異なり、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] にはチェック ボックス コンテンツ コントロールを表す特定の型が用意されていません。 つまり、CheckBoxContentControl 型はありません。 ただし、プログラム上でジェネリック型の <xref:Microsoft.Office.Tools.Word.ContentControl> を文書に追加し、チェック ボックス コンテンツ コントロールを作成することはできます。 詳細については、次を参照してください。 [Word プロジェクトでのチェック ボックス コンテンツ コントロール](#checkbox)です。  
  
### <a name="combo-box"></a>コンボ ボックス  
 コンボ ボックスには、ユーザーが選択できるアイテムの一覧が表示されます。 ドロップダウン リストとは異なり、コンボ ボックスではユーザーが独自のアイテムを追加できます。 詳細については、<xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> 型を参照してください。  
  
### <a name="date-picker"></a>日付の選択  
 日付選択は、日付を選択するためのカレンダー UI を提供します。 このカレンダーは、エンド ユーザーがコントロール内のドロップダウン矢印をクリックしたときに表示されます。 地域別カレンダーやさまざまな日付形式を使用できます。 詳細については、<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> 型を参照してください。  
  
### <a name="drop-down-list"></a>ドロップダウン リスト  
 ドロップダウン リストには、ユーザーが選択できるアイテムの一覧が表示されます。 コンボ ボックスとは異なり、ドロップダウン リストではユーザーがアイテムの追加や編集を行うことはできません。 詳細については、<xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 型を参照してください。  
  
### <a name="group"></a>グループ  
 グループ コントロールは、文書の中にユーザーが編集や削除を行うことができない (保護された) 領域を定義します。 グループ コントロールには、任意のドキュメント アイテム (テキスト、表、グラフィックス、およびその他のコンテンツ コントロール) を含めることができます。 詳細については、<xref:Microsoft.Office.Tools.Word.GroupContentControl> 型を参照してください。  
  
### <a name="picture"></a>画像  
 画像コントロールには、画像が表示されます。 イメージは、デザイン時または実行時に指定できます。また、ユーザーがこのコントロールをクリックしてイメージを選択し、文書に挿入することもできます。 詳細については、<xref:Microsoft.Office.Tools.Word.PictureContentControl> 型を参照してください。  
  
### <a name="rich-text"></a>リッチ テキスト形式  
 リッチ テキスト コントロールには、テキストやその他のアイテム (表、画像、またはその他のコンテンツ コントロール) を含めることができます。 詳細については、<xref:Microsoft.Office.Tools.Word.RichTextContentControl> 型を参照してください。  
  
### <a name="plain-text"></a>プレーンテキスト  
 プレーンテキスト コントロールには、テキストが格納されます。 プレーンテキスト コントロールにその他のアイテム (表、画像、またはその他のコンテンツ コントロール) を含めることはできません。 また、プレーンテキスト コントロール内のすべてのテキストには同じ書式が設定されます。 たとえば、プレーンテキスト コントロールに含まれる文の 1 つの単語に斜体を適用すると、そのコントロールに含まれるすべてのテキストに斜体が適用されます。 詳細については、<xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 型を参照してください。  
  
### <a name="generic-content-control"></a>汎用コンテンツ コントロール  
 汎用コンテンツ コントロールは、使用可能な任意の種類のコンテンツ コントロールを表すことができる <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトです。 <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> プロパティを使用して <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを変更すると、別の種類のコンテンツ コントロールのように動作させることができます。 たとえば、プレーンテキスト コントロールを表す <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成した場合は、実行時にそのオブジェクトを変更して、コンボ ボックスのように動作させることができます。  
  
 <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成できるのは、実行時だけです。デザイン時には作成できません。 詳細については、次を参照してください。[する方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)です。  
  
## <a name="common-features-of-content-controls"></a>コンテンツ コントロールの共通機能  
 ほとんどのコンテンツ コントロールは、一般的なタスクの実行に使用できるメンバー セットを共有しています。 これらのメンバーを使用して実行できるタスクの一部について、次の表で説明します。  
  
|タスク :|方法 :|  
|--------------------|--------------|  
|コントロールに表示されるテキストを取得または設定する。|使用して、**テキスト**プロパティです。 **注:** 、<xref:Microsoft.Office.Tools.Word.PictureContentControl>と<xref:Microsoft.Office.Tools.Word.ContentControl>型には、このプロパティはありません。|  
|ユーザーによるコントロールの編集、データ ソースからコントロールへのデータの読み込み、またはコントロールの内容の削除が行われるまでコントロールに表示される一時的なテキストを取得または設定します。|使用して、 **PlaceholderText**プロパティです。 **注:** 、<xref:Microsoft.Office.Tools.Word.PictureContentControl>型には、このプロパティはありません。|  
|ユーザーがクリックしたときにコンテンツ コントロールの境界線に表示されるタイトルを取得または設定します。|使用して、**タイトル**プロパティです。|  
|ユーザーがコントロールを編集した後で、文書からコントロールを自動的に削除します。  (コントロール内のテキストは文書内に残ります。)|使用して、**一時**プロパティです。|  
|ユーザーがコンテンツ コントロールをクリックしたとき、またはプログラムによってカーソルがコンテンツ コントロールに移動したときに、コードを実行します。|コントロールの <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> イベントを処理します。|  
|ユーザーがコンテンツ コントロールの外部をクリックしたとき、またはプログラムによってカーソルがコンテンツ コントロールの外部に移動したときに、コードを実行します。|コントロールの <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> イベントを処理します。|  
|元に戻す操作またはやり直し操作の結果としてコンテンツ コントロールが文書に追加された後で、コードを実行します。|コントロールの <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> イベントを処理します。|  
|コンテンツ コントロールが文書から削除される直前にコードを実行します。|コントロールの <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> イベントを処理します。|  
  
##  <a name="Protection"></a>コンテンツ コントロールを使用して文書の一部を保護します。  
 文書の一部を保護すると、ユーザーは文書のその部分のコンテンツを変更および削除できなくなります。 コンテンツ コントロールを使用して文書の一部を保護するには、いくつかの方法があります。  
  
 保護対象とする領域がコンテンツ コントロールの内部にある場合は、コンテンツ コントロールのプロパティを使用して、ユーザーがコントロールの編集や削除を行うことができないようにします。  
  
-   **LockContents**プロパティは、内容を編集できないようにします。  
  
-   **[Lockcontentcontrol]**プロパティがコントロールを削除できないようにします。  
  
 保護対象とする領域がコンテンツ コントロールの内部にない場合、またはコンテンツ コントロールとその他の種類のコンテンツを含む領域を保護する場合は、領域全体を <xref:Microsoft.Office.Tools.Word.GroupContentControl> に配置します。 他のコンテンツ コントロールとは異なり、<xref:Microsoft.Office.Tools.Word.GroupContentControl> にはユーザーに対して表示される UI がありません。 このコントロールは、ユーザーが編集できない領域を定義することだけを目的としています。  
  
> [!NOTE]  
>  コンテンツ コントロールが埋め込まれた <xref:Microsoft.Office.Tools.Word.GroupContentControl> を作成した場合、埋め込まれたコンテンツ コントロールは自動的には保護されません。 使用する必要があります、 **LockContents**の各プロパティには、ユーザーがその内容を編集することを防止するコントロールが埋め込まれています。  
  
 コンテンツ コントロールを使用して、ドキュメントの一部を保護する方法の詳細については、次を参照してください。[する方法: 文書を保護するコンテンツ コントロールの使用によって](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)です。  
  
##  <a name="DataBinding"></a>コンテンツ コントロールへのデータをバインディング  
 コンテンツ コントロールをデータ ソースにバインドすると、文書内にデータを表示できます。 データ ソースが更新されると、コンテンツ コントロールに変更内容が反映されます。 変更内容をデータ ソースに反映させて保存することもできます。  
  
 コンテンツ コントロールには、次のようなデータ バインディング オプションがあります。  
  
-   Windows フォームと同じデータ バインディング モデルを使用して、データベース フィールドやマネージ オブジェクトにコンテンツ コントロールをバインドできます。  
  
-   内の XML の要素にコンテンツ コントロールをバインドすることができます (とも呼ば*カスタム XML 部分*) ドキュメントに埋め込まれています。  
  
 Office ソリューションにおけるデータへのホスト コントロールのバインドの概要については、次を参照してください。 [Office ソリューションでのコントロールへのデータ バインディング](../vsto/binding-data-to-controls-in-office-solutions.md)です。  
  
### <a name="using-the-windows-forms-data-binding-model"></a>Windows フォームのデータ バインディング モデルの使用  
 ほとんどのコンテンツ コントロールは、Windows フォームが使用する単純なデータ バインディング モデルをサポートします。 単純なデータ バインディングとは、コントロールが単一のデータ要素 (データ テーブルの列の値など) にバインドされることを意味します。 詳細については、「 [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)」を参照してください。  
  
 ドキュメント レベルのプロジェクトでできるデータをバインドするコンテンツ コントロールを使用して、**データソース**ウィンドウ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 コンテンツのデータ バインド コントロールをドキュメントに追加する方法の詳細については、次を参照してください。[する方法: データをデータベースからドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)と[する方法: ドキュメント オブジェクトのデータを読み込む](../vsto/how-to-populate-documents-with-data-from-objects.md)します。  
  
 次の表では、各データ型にバインドできるコンテンツ コントロールの一覧、**データソース**ウィンドウです。  
  
|データの種類|既定のコンテンツ コントロール|このデータ型にバインドできるその他のコンテンツ コントロール|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> 配列|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|なし|  
  
 ドキュメント レベルのプロジェクトおよび VSTO アドイン プロジェクトでは、コントロールの <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティの <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> メソッドを使用して、プログラムによってデータ ソースにコンテンツ コントロールをバインドできます。 これを行う場合、文字列で渡す**テキスト**を*propertyName*のパラメーター、<xref:System.Windows.Forms.ControlBindingsCollection.Add%2A>メソッドです。 **テキスト**プロパティは、コンテンツ コントロールの既定のデータ バインディング プロパティ。  
  
 コンテンツ コントロールは双方向のデータ バインディングもサポートするため、コントロール内での変更によってデータ ソースが更新されます。 詳細については、「 [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)」を参照してください。  
  
> [!NOTE]  
>  コンテンツ コントロールは複合データ バインディングをサポートしません。 Windows フォーム データ モデルを使用してデータ ソースに <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> または <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> をバインドすると、ユーザーがコントロールをクリックしたときに 1 つの値だけが表示されます。 これらのコントロールを一連のデータ値にバインドし、ユーザーがその中から選択できるようにするには、カスタム XML 部分の要素にコントロールをバインドします。  
  
### <a name="binding-content-controls-to-custom-xml-parts"></a>カスタム XML 部分へのコンテンツ コントロールのバインディング  
 一部のコンテンツ コントロールは、文書に埋め込まれているカスタム XML 部分の要素にバインドできます。 カスタム XML 部分の詳細については、次を参照してください。[カスタム XML 部分の概要](../vsto/custom-xml-parts-overview.md)です。  
  
 コンテンツ コントロールをカスタム XML 部分の要素にバインドするには、使用、 **XMLMapping**コントロールのプロパティです。 次のコード例は、文書に既に追加されているカスタム XML 部分の `Product` ノードの下にある `Price` 要素に <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> をバインドする方法を示しています。  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 さらに詳しくカスタム XML 部分へのコンテンツ コントロールをバインドする方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)です。  
  
 カスタム XML 部分にコンテンツ コントロールをバインドすると、双方向のデータ バインディングが自動的に有効になります。 ユーザーがコントロール内のテキストを編集すると、対応する XML 要素が自動的に更新されます。 同様に、カスタム XML 部分の要素の値が変更されると、その XML 要素にバインドされているコンテンツ コントロールに新しいデータが表示されます。  
  
 カスタム XML 部分にバインドできるコンテンツ コントロールの種類を次に示します。  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-binding-events-for-content-controls"></a>コンテンツ コントロールのデータ バインディング イベント  
 すべてのコンテンツ コントロールは、データ関連のタスク (データ ソースを更新する前にコントロール内のテキストが特定の条件を満たしているかどうかの検証など) を実行するために処理できる一連のイベントを提供します。 データ バインディングに関連するコンテンツ コントロール イベントの一覧を、次の表に示します。  
  
|タスク|event|  
|----------|-----------|  
|カスタム XML 部分にバインドされているコンテンツ コントロール内のテキストが Word で自動的に更新される直前に、コードを実行します。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|コンテンツ コントロールにバインドされているカスタム XML 部分内のデータが Word で自動的に更新される直前 (コンテンツ コントロール内のテキストが変更された後) に、コードを実行します。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|独自のコードを実行し、独自の条件に基づいてコントロールの内容を検証します。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|コントロールの内容が正常に検証された後で、コードを実行します。|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>コンテンツ コントロールの制限事項  
 Office プロジェクトでコンテンツ コントロールを使用する場合は、次の制限事項に留意してください。  
  
### <a name="behavior-differences-between-design-time-and-run-time"></a>デザイン時と実行時の動作の違い  
 実行時のコンテンツ コントロールに対する Microsoft Office Word の制約の多くは、デザイン時には適用されません。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でドキュメント レベルのソリューションの UI を設計するときは、必ず実行時にサポートされる方法だけを使用してコンテンツ コントロールを編集してください。  
  
 デザイン時のコンテンツ コントロールの変更方法が実行時にサポートされない場合、サポートされない変更であることを示す [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デザイナーの警告は表示されません。 ただし、プロジェクトをデバッグまたは実行したときや、プロジェクトを保存してから再度開いた場合は、Word のエラー メッセージと文書を修復するかどうかの確認メッセージが表示されます。 文書を修復すると、サポートされていないすべてのコンテンツと書式設定がコントロールから削除されます。  
  
 たとえば、Word ではデザイン時に <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> に表を追加することを妨げません。 しかし、実行時には <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> オブジェクトに表を含めることができないため、文書を開くと Word のエラー メッセージが表示されます。  
  
 コンテンツ コントロールの動作を定義する多くのプロパティはデザイン時に効果がないことにも留意してください。 例では、設定した場合の**LockContents**にコンテンツ コントロールのプロパティの**True**でコントロール内のテキストを編集できます、デザイン時に、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デザイナー。 このプロパティによってユーザーがコントロールを編集できなくなるのは、実行時だけです。  
  
### <a name="event-limitations"></a>イベントの制限事項  
 コンテンツ コントロールは、ユーザーがコントロール内のテキストまたはその他のアイテムを変更したときに発生するイベントを提供しません。 たとえば、ユーザーが <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> や <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> で異なるアイテムを選択したときに発生するイベントはありません。  
  
 ユーザーがコンテンツ コントロールの内容を編集した時点を判断するには、コントロールをカスタム XML 部分にバインドし、<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> イベントを処理します。 このイベントは、ユーザーがカスタム XML 部分にバインドされているコントロールの内容を変更したときに発生します。 カスタム XML 部分にコンテンツ コントロールをバインドする方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: カスタム XML 部分へのコンテンツ コントロールのバインド](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)です。  
  
###  <a name="checkbox"></a>Word プロジェクトでのチェック ボックス コンテンツ コントロール  
 Word 2010 では、チェック ボックスを表す新しい種類のコンテンツ コントロールが導入されました。 ただし、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office プロジェクトで使用するための対応する CheckBoxContentControl 型を行いません。 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] または Word 2010 プロジェクトでチェック ボックス コンテンツ コントロールを作成するには、<xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> メソッドを使用して <xref:Microsoft.Office.Tools.Word.ContentControl> オブジェクトを作成し、<xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> の値をそのメソッドに渡してチェック ボックス コンテンツ コントロールを指定します。 これを実行する方法を次のコード例に示します。  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>参照  
 [拡張オブジェクトによる Word の自動化](../vsto/automating-word-by-using-extended-objects.md)   
 [方法: Word 文書にコンテンツ コントロールを追加](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [チュートリアル: コンテンツ コントロールによるテンプレートの作成](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Office ソリューションにおけるデータ](../vsto/data-in-office-solutions.md)   
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [ホスト項目およびホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
