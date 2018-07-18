---
title: Outlook フォーム領域の作成に関するガイドライン
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfbe02c652c53f0b7e5b2322ce76e7c022487d2e
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548168"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Outlook フォーム領域を作成するのには、ガイドライン
  次に示す情報は、フォーム領域の最適化と、潜在的な問題の回避に役立ちます。  
  
-   [フォーム領域の名前を使用して](#UsingFormRegions)です。  
  
-   [フォーム領域の継承を無効にする](#DisablingInheritance)です。  
  
-   [種類を理解して、メッセージ クラス名](#ClassNames)です。  
  
-   [閲覧ウィンドウのフォーム領域に隣接デザイン](#ReadingPane)です。  
  
-   [最適なアイコン サイズを使用して](#UsingOptimal)です。  
  
 フォーム領域の詳細については、次を参照してください。[作成 Outlook フォーム領域の](../vsto/creating-outlook-form-regions.md)します。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> フォーム領域の名前を使用します。  
 フォーム領域は、いくつかの名前を使用して記述されます。 これらの名前の違いと、その名前がフォーム領域に与える影響を理解することが大切です。 次の表は、それぞれの名前の説明です。  
  
|フォーム領域の名前|説明|  
|----------------------|-----------------|  
|フォーム領域の項目名|**[新しい項目の追加]** ダイアログ ボックスで **Outlook フォーム領域** のアイテムに指定した名前です。 これはフォーム領域コード ファイルの名前で、 **ソリューション エクスプローラー**に表示されます。|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> プロパティ|この名前は、 **新しい Outlook フォーム領域** ウィザードの **[説明用のテキストを指定し、表示設定を選択します]** ページで指定します。 この名前は、 **[プロパティ]** ウィンドウに **FormRegionName** プロパティとして表示されます。<br /><br /> <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> プロパティを使用して、Outlook ユーザー インターフェイス (UI) のフォーム領域を識別するラベルを指定します。 分離フォーム領域の場合、この名前は Outlook アイテムのリボンにボタンとして表示されます。<br /><br /> 隣接フォーム領域の場合、この名前は、フォーム領域上のヘッダー テキストとして表示されます。|  
|`Microsoft.Office.Tools.Outlook.FormRegionName` 属性|プロジェクトに **Outlook フォーム領域** アイテムを追加すると、Visual Studio によって、このプロパティはフォーム領域の完全修飾名に設定されます。 既定の完全修飾名は、VSTO アドインの名前にフォーム領域の名前を追加して、ドットで区切った名前に設定されます。たとえば、 `OutlookAddIn1.FormRegion1`のようになります。<br /><br /> この完全修飾名は、フォーム領域ファクトリ クラスの先頭にも属性として表示されます。<br /><br /> 使用して、 `Microsoft.Office.Tools.Outlook.FormRegionName` Outlook VSTO アドインをすべてを通じてフォーム領域を一意に識別する属性。値を変更することはできません、`Microsoft.Office.Tools.Outlook.FormRegionName`属性フォーム領域アイテムの名前を変更して、または変更することによって、<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>プロパティです。 この名前を変更する必要がありますを変更する、`Microsoft.Office.Tools.Outlook.FormRegionName`フォーム領域コード ファイル内の属性です。|  
  
##  <a name="DisablingInheritance"></a> フォーム領域の継承を無効にします。  
 既定では、カスタム メッセージ クラスは、基本メッセージ クラスのすべてのフォーム領域の関連付けを継承します。 たとえば、メッセージ クラスの名前付き`IPM.Task.Contoso`から派生した`IPM.Task`です。 したがって、`IPM.Task.Contoso`のフォーム領域の関連付けを継承`IPM.Task`です。  
  
 どの派生メッセージ クラスにもフォーム領域を関連付ける必要がない場合は、フォーム領域の <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> プロパティを **true**。 隣接フォーム領域に関連付ける場合など、`IPM.Task`設定と、<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A>プロパティを**true**、フォーム領域は、標準タスク フォームの下部にのみ追加されます。 フォーム領域は、標準タスク フォームのカスタマイズ バージョンの末尾には追加されません。  
  
##  <a name="ClassNames"></a> 種類とメッセージ クラス名を理解します。  
 Outlook アイテムの型名は、Outlook アイテムのメッセージ クラス名とは異なります。 たとえば、RSS アイテムの種類名は`Microsoft.Office.Interop.Outlook.PostItem`します。 RSS アイテムのメッセージ クラス名は`IPM.Post.RSS`します。  
  
 型名は、コード内の Outlook アイテムを参照するときに使用します。 型名の一覧は、次を参照してください。[フォーム領域を Outlook メッセージ クラスに関連付ける](../vsto/associating-a-form-region-with-an-outlook-message-class.md)です。  
  
 **新しい Outlook フォーム領域ウィザード** の Outlook アイテムのメッセージ クラス名は、アイテムをフォーム領域に関連付けるときに使用します。 有効なメッセージ クラス名の一覧は、次を参照してください。[フォーム領域を Outlook メッセージ クラスに関連付ける](../vsto/associating-a-form-region-with-an-outlook-message-class.md)です。  
  
##  <a name="ReadingPane"></a> 閲覧ウィンドウの隣接フォーム領域のデザイン  
 Outlook の閲覧ウィンドウを使用すると、アイテムを開かずに、Outlook アイテムをプレビューできます。 閲覧ウィンドウは、読み取り専用に設計されています。 そのため、隣接フォーム領域に追加するテキスト ボックスなどの入力コントロールは、閲覧ウィンドウでアイテムとフォーム領域を開いたときに、期待どおりに動作しないことがあります。  
  
 たとえば、隣接フォーム領域を含むアイテムを閲覧ウィンドウで開くと、次のような状況が発生する可能性があります。  
  
1.  フォーム領域上のテキスト ボックスで、一部のテキストを選択します。  
  
2.  キーを押して**削除**です。  
  
3.  テキスト ボックスで選択したテキスト部分でなく、メール アイテム全体が削除されます。  
  
 隣接フォーム領域をデザインするときに、その領域に入力コントロールを含める場合は、閲覧ウィンドウ内のコントロールをテストして、正しく動作することを確認します。 期待どおりに動作しないコントロールを無効にするように、カスタム コードを追加することを検討してください。  
  
 または、フォーム領域の <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> プロパティを **False**。 この方法では、閲覧ウィンドウでフォーム領域が使用できなくなります。  
  
##  <a name="UsingOptimal"></a> 最適なアイコン サイズを使用します。  
 **[プロパティ]** ウィンドウの **[Icons]** プロパティ グループでアイコンのプロパティを設定すると、フォーム領域に表示するアイコンを指定できます。 視覚的な品質を最高にするために、次のガイドラインを参考にしてください。  
  
-   **ページ** アイコンには、PNG (Portable Network Graphics) ファイルを使用します。  
  
-   **ウィンドウ** アイコンは 32 ピクセル × 32 ピクセルにする必要があります。  
  
-   その他のすべてのアイコンは 16 ピクセル × 16 ピクセルにする必要があります。  
  
 **ページ** アイコンは、分離、置換、またはすべて置換のフォーム領域を含むアイテムについて、インスペクターのリボンに表示されます。  
  
 **ウィンドウ**アイコンに表示されます、通知領域で、 **Alt**+**タブ**その表示置換、またはすべて置換フォーム項目を開く ダイアログ ボックス領域。  
  
## <a name="see-also"></a>関連項目  
 [実行時にフォーム領域にアクセスします。](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook フォーム領域を作成します。](../vsto/creating-outlook-form-regions.md)   
 [チュートリアル: Outlook フォーム領域をデザインします。](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [方法: フォーム領域を Outlook アドイン プロジェクトに追加します。](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [フォーム領域を Outlook メッセージ クラスに関連付ける](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  