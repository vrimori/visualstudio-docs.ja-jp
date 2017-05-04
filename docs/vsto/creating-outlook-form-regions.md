---
title: "Outlook フォーム領域の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "フォーム領域 [Visual Studio での Office 開発]"
  - "フォーム領域 [Visual Studio での Office 開発], 作成"
  - "Outlook [Visual Studio での Office 開発], フォーム領域"
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Outlook フォーム領域の作成
  フォーム領域を使用して、Microsoft Office Outlook フォームをカスタマイズできます。  Visual Studio には、フォーム領域のデザイン、開発、およびデバッグを簡単に行うことができる高度なツールが用意されています。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ここでは、次の情報について説明します。  
  
-   [フォーム領域を使用する利点](#Enhance)  
  
-   [プロジェクトへの Outlook フォーム領域の追加](#Adding)  
  
-   [フォーム領域デザイナーの使用方法](#UsingFormRegionDesigner)  
  
-   [Outlook でデザインしたフォーム領域の使用方法](#UsingFormRegionDesignedOutlook)  
  
-   [フォーム領域へのカスタム コードの追加](#AddingCustomCode)  
  
-   [プロジェクトのビルド](#Building)  
  
-   [フォーム領域のデバッグ](#Debugging)  
  
-   [フォーム領域の配置](#Deploying)  
  
##  <a name="Enhance"></a> フォーム領域を使用する利点  
 フォーム領域は、従来の Outlook フォーム開発に多くの機能強化をもたらします。  
  
-   標準フォームの既定のページをカスタマイズする。  
  
-   標準フォームに最大 12 ページ追加する。  
  
-   標準フォームを置換または拡張する。  
  
-   閲覧ペインとインスペクターにカスタム UI を表示する。  
  
 詳細については、「[フォーム ページおよびフォーム領域のカスタマイズ](HV10038632)」を参照してください。  
  
##  <a name="Adding"></a> プロジェクトへの Outlook フォーム領域の追加  
 **新しい Outlook フォーム領域**ウィザードを使用して、新しいフォーム領域をデザインしたり、Outlook でデザインしたフォーム領域をインポートしたりできます。  また、別の Outlook VSTO アドイン プロジェクトで使用したフォーム領域がある場合は、既存のフォーム領域を再利用できます。  
  
###  <a name="CreatingFormRegion"></a> ウィザードを使用した新しいフォーム領域の作成  
 フォーム領域を作成するには、Outlook VSTO アドイン プロジェクトに **Outlook フォーム領域**アイテムを追加します。  これによって、**新しい Outlook フォーム領域**ウィザードが起動します。  
  
 このウィザードでは、新しいフォーム領域をデザインするか、Outlook でデザインしたフォーム領域をインポートするかを指定します。  新しいフォーム領域のデザインの詳細については、「[フォーム領域デザイナーの使用方法](#UsingFormRegionDesigner)」を参照してください。  Outlook でデザインしたフォーム領域の使用方法の詳細については、「[Outlook でデザインしたフォーム領域のインポート](#UsingFormRegionDesignedOutlook)」を参照してください。  
  
 このウィザードでは、作成するフォーム領域の種類を指定します。  フォーム領域の種類について、次の表で説明します。  
  
|領域の種類|説明|  
|-----------|--------|  
|分離|フォーム領域を Outlook フォームの新しいページとして追加します。|  
|隣接|フォーム領域を Outlook フォームの既定のページの下部に追加します。|  
|Replacement|フォーム領域を Outlook フォームの既定のページに代わる新しいページとして追加します。|  
|すべて置換|Outlook フォーム全体をフォーム領域に置き換えます。|  
  
 このウィザードでは、表示条件を指定し、拡張するフォームの種類を選択することもできます。  詳細については、「[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)」を参照してください。  
  
 このウィザードで行った選択は、他のウィザード ページで使用できるオプションに影響します。  たとえば、**\[新しい Outlook フォーム領域の作成\]** ページで **\[隣接\]** または **\[分離\]** を選択すると、**\[説明用のテキストを指定し、表示設定を選択します\]** ページの **\[タイトル\]** フィールドと **\[説明\]** フィールドは使用できません。  これは、隣接または分離フォーム領域を表示するときに、Outlook ではこれらのフィールドを使用しないためです。  
  
#### フォーム領域ファイル  
 **新しい Outlook フォーム領域**ウィザードを完了すると、Visual Studio によって以下のファイルがプロジェクトに自動的に追加されます。  
  
-   フォーム領域コード ファイル。  このファイルには、**\[新しい項目の追加\]** ダイアログ ボックスで **Outlook フォーム領域**アイテムに指定した名前が付けられます。  このファイルには、フォーム領域イベントを処理するコードを追加します。  
  
-   フォーム領域デザイナー コード ファイル。  このファイルは、フォーム領域デザイナーによって生成されたコードを含んでおり、直接編集すべきではありません。  
  
-   Outlook Form Storage \(.ofs\) ファイル。  
  
    > [!NOTE]  
    >  このファイルがプロジェクトに追加されるのは、Outlook でデザインしたフォーム領域をインポートした場合だけです。  
  
#### フォーム領域ファクトリ クラス  
 フォーム領域コード ファイルには、<xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> インターフェイスを実装する部分クラスが含まれています。  これがフォーム領域ファクトリ クラスです。  フォーム領域ファクトリ クラスは、フォーム領域の新しいインスタンスを作成するために使用します。  
  
 このクラスを見つけるには、**\[フォーム領域ファクトリ\]** 領域を展開します。  
  
 このクラスには、**新しい Outlook フォーム領域**ウィザードによって、フォーム領域の内部名とフォーム領域を表示するメッセージ クラスを指定する属性が追加されます。  これらの属性は、ファイルがプロジェクトに追加された後、手動で変更できます。  
  
 フォーム領域ファクトリ クラスの大部分は、フォーム領域デザイナー ファイルに実装されます。  ただし、`FormRegionInitializing` イベント ハンドラーはフォーム領域コード ファイルに公開されます。  このイベント ハンドラーを使用して、Outlook がフォーム領域を表示するかどうかを指定できます。  詳細については、「[フォーム領域イベントの処理](#HandlingFormRegionEvents)」を参照してください。  
  
###  <a name="AddingExistingFormRegion"></a> プロジェクトへの既存のフォーム領域の追加  
 別の Outlook プロジェクトで使用した Outlook フォーム領域がある場合は、**\[既存項目の追加\]** ダイアログ ボックスを使用して、そのフォーム領域を現在の Outlook VSTO アドイン プロジェクトで再利用できます。  
  
 既存のフォーム領域にはコード ファイル \(.vb または .cs\) が必要です。**\[既存項目の追加\]** ダイアログ ボックスで Outlook Form Storage \(.ofs\) ファイルを追加することはできません。  ただし、Outlook Form Storage ファイルをインポートすることによって新しいフォーム領域を作成できます。  詳細については、「[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)」を参照してください。  
  
##  <a name="UsingFormRegionDesigner"></a> フォーム領域デザイナーの使用方法  
 フォーム領域デザイナーでは、フォーム領域のレイアウトと外観をデザインできます。  マネージ コントロールをデザイナーの画面にドラッグし、コントロールをダブルクリックしてイベント ハンドラーを開き、**\[プロパティ\]** ウィンドウでプロパティを設定することができます。  
  
> [!NOTE]  
>  Outlook でのフォーム領域の表示方法に関連するプロパティは、**\[プロパティ\]** ウィンドウの **\[マニフェスト\]** ノードの下にあります。  
  
 フォーム領域デザイナーを使用できるのは、**新しい Outlook フォーム領域**ウィザードの **\[フォーム領域を作成する方法の選択\]** ページで **\[新しいフォーム領域のデザイン\]** を選択した場合だけです。  
  
 フォーム領域デザイナーを開くには、次の 3 つの方法があります。  
  
-   **ソリューション エクスプローラー**でフォーム領域コード ファイルをダブルクリックする。  
  
-   **ソリューション エクスプローラー**で、フォーム領域コード ファイルを右クリックし、**\[デザイナーの表示\]** をクリックする。  
  
-   **ソリューション エクスプローラー**でフォーム領域コード ファイルを選択し、**\[表示\]** メニューの **\[デザイナー\]** をクリックする。  
  
 フォーム領域デザイナーは、マネージ コントロールのみをサポートしています。  ネイティブな Outlook コントロールを追加することはできません。  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Outlook でデザインしたフォーム領域のインポート  
 Outlook でデザインする際に、ネイティブな Outlook コントロールをフォーム領域に追加できます。  ネイティブな Outlook コントロールは、デザイン時に Outlook データにバインドできます。  ただし、その場合はフォーム領域デザイナーを使用してマネージ コントロールを追加したりフォーム領域のデザインを変更したりすることはできません。  
  
 **新しい Outlook フォーム領域**ウィザードを使用して、フォーム領域を Outlook VSTO アドイン プロジェクトにインポートできます。  **\[フォーム領域を作成する方法の選択\]** ページで **\[Outlook Form Storage \(.ofs\) ファイルのインポート\]** を選択します。  次に、Outlook Form Storage \(.ofs\) ファイルの場所を参照します 。  \(フォーム領域は .ofs ファイルとして保存されます。\)  
  
 **新しい Outlook フォーム領域**ウィザードが .ofs ファイルをプロジェクト ディレクトリにコピーし、コントロールの参照をフォーム領域デザイナー ファイルに追加します。  これで、フォーム領域コード ファイルでコントロールのイベントを処理できます。  
  
 Visual Basic プロジェクトでイベントを処理するには、コード エディターの上部にあるメソッド名リストからイベントを選択します。  
  
 C\# プロジェクトでイベントを処理するには、<xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> メソッドでコントロール イベントにサブスクライブします。  詳細については、「[方法 : イベント サブスクリプションとサブスクリプションの解除 &#40;C&#35; プログラミング ガイド&#41;](../Topic/How%20to:%20Subscribe%20to%20and%20Unsubscribe%20from%20Events%20(C%23%20Programming%20Guide).md)」を参照してください。  
  
 フォーム領域のプロパティは、フォーム領域ファクトリ クラスの `InitializeManifest` メソッドで変更できます。  
  
> [!NOTE]  
>  フォーム領域をインポートするには、開発用コンピューターにインストールされている Outlook と同じバージョンの Outlook を対象とするプロジェクトで作業している必要があります。  たとえば、Outlook 2010 がインストールされている場合、フォーム領域のインポートは **Outlook 2010 アドイン** プロジェクト テンプレートを使用して作成されたプロジェクトでのみ機能します。  
  
### インポートしたフォーム領域のデザインの更新  
 フォーム領域に対して、コントロールの追加、削除、または変更を行うことができます。  これを行う前に、フォーム領域コード ファイルに追加したコードをバックアップします。  その後、Outlook で .ofs ファイルを開き、フォーム領域を変更し、変更を保存します。  **新しい Outlook フォーム領域**ウィザードを使用して、変更した .ofs ファイルをインポートします。  その後、新しいフォーム領域コード ファイルにコードを貼り付けることができます。  
  
##  <a name="AddingCustomCode"></a> フォーム領域へのカスタム コードの追加  
 <xref:Microsoft.Office.Tools.Outlook> 名前空間では、フォーム領域、フォーム領域を表示する Outlook アイテム、およびその他の役に立つアイテムを表すクラスにアクセスできます。  **Outlook フォーム領域**アイテムによって、自動的にこのアセンブリへの参照がプロジェクトに追加され、**using** または **Imports** ステートメントがフォーム領域コード ファイルの先頭に挿入されます。  
  
 Microsoft.Office.Interop.Outlook 名前空間のクラス、メソッド、およびプロパティを使用して、ほとんどの Outlook プログラミング タスクを実行できます。  Outlook オブジェクト モデルの詳細については、「[Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)」を参照してください。  Outlook オブジェクト モデルを利用する一般的なタスクの例については、「[Outlook ソリューション](../vsto/outlook-solutions.md)」を参照してください。  
  
###  <a name="HandlingFormRegionEvents"></a> フォーム領域イベントの処理  
 **Outlook フォーム領域**アイテムによって、自動的に次の 3 つのイベント ハンドラーがフォーム領域コード ファイルに追加されます。  
  
|イベント|説明|  
|----------|--------|  
|FormRegionInitializing|フォーム領域が初期化される前に発生します。  このイベント ハンドラーの状態をチェックして、Outlook がフォーム領域を表示する必要があるかどうかを判定できます。  詳細については、「[方法 : Outlook にフォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)」を参照してください。|  
|FormRegionShowing|フォーム領域のインスタンスが作成されてから、フォーム領域が表示される前までの間に発生します。|  
|FormRegionClosed|フォーム領域が閉じられる前に発生します。|  
  
##  <a name="Building"></a> プロジェクトのビルド  
 フォーム領域を含む Outlook VSTO アドイン プロジェクトをビルドすると、Visual Studio によってレジストリに次の情報が追加されます。  
  
-   1 つ以上のフォーム領域に関連付けられている各メッセージ クラスのキー。  
  
-   各フォーム領域のエントリと、Outlook VSTO アドインの名前を表す関連値。  
  
 この情報は、Outlook がフォーム領域を読み込むときに使用されます。  
  
##  <a name="Debugging"></a> フォーム領域のデバッグ  
 フォーム領域を含む Outlook VSTO アドインは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトと同じようにデバッグできます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを起動すると、Visual Studio によって自動的に Outlook が起動されます。  
  
 フォーム領域を表示するには、対応する Outlook アイテムを開く必要があります。  たとえば、隣接フォーム領域をメール アイテムの下部に追加する場合は、メール アイテムを開きます。  
  
##  <a name="Deploying"></a> フォーム領域の配置  
 フォーム領域は、関連付けられた Outlook VSTO アドインと共に自動的に配置されます。  したがって、フォーム領域を配置するための特別な作業を実行する必要はありません。  VSTO アドインの配置の詳細については、「[Office ソリューションの配置](../vsto/deploying-an-office-solution.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[Outlook フォーム領域の作成に関するガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)|フォーム領域を最適化し、発生する可能性のある問題を回避するのに役立つ情報を提供します。|  
|[方法 : フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|**新しい Outlook フォーム領域**ウィザードを使用して、標準またはカスタムの Microsoft Office Outlook フォームを拡張するフォーム領域を作成する方法について説明します。|  
|[フォーム領域の Outlook メッセージ クラスへの関連付け](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|フォーム領域を各アイテムのメッセージ クラスに関連付けることにより、そのフォーム領域を表示する Microsoft Office Outlook アイテムを指定する方法について説明します。|  
|[チュートリアル : Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)|連絡先アイテムのインスペクター ウィンドウに新しいページとして表示するカスタム フォーム領域をデザインする方法について説明します。|  
|[チュートリアル : Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Microsoft Office Outlook でフォーム領域をデザインし、**新しい Outlook フォーム領域**ウィザードを使用して Outlook VSTO アドイン プロジェクトにフォーム領域をインポートする方法について説明します。|  
|[実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)|コードを記述して、フォーム領域でコントロールの表示、非表示、変更を行う方法と、`Globals` クラスを使用して、記述したコードをユーザーがプロジェクト内の他の領域から実行できるようにする方法について説明します。|  
|[方法 : Outlook にフォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Microsoft Office Outlook で特定のアイテムのフォーム領域が表示されないようにする方法について説明します。|  
|フォーム領域が表示される Outlook アイテムにアクセスする方法について説明します。|  
|[Outlook フォーム領域のカスタム動作](../vsto/custom-actions-in-outlook-form-regions.md)|ユーザーが Outlook アイテムに応答できるようにする方法について説明します。|  
  
  