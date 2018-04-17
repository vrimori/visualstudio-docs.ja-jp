---
title: Outlook フォーム領域の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 550514444e7931b188951bbf05f8d371bc361aca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="creating-outlook-form-regions"></a>Creating Outlook Form Regions
  フォーム領域を使用して、Microsoft Office Outlook フォームをカスタマイズできます。 Visual Studio には、フォーム領域のデザイン、開発、およびデバッグを簡単に行うことができる高度なツールが用意されています。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ここでは、次の情報について説明します。  
  
-   [フォーム領域を使用する利点](#Enhance)  
  
-   [Outlook フォーム領域をプロジェクトに追加します。](#Adding)  
  
-   [フォーム領域デザイナーを使用します。](#UsingFormRegionDesigner)  
  
-   [Outlook でデザインしたフォーム領域を使用します。](#UsingFormRegionDesignedOutlook)  
  
-   [フォーム領域へのカスタム コードを追加します。](#AddingCustomCode)  
  
-   [プロジェクトのビルド](#Building)  
  
-   [フォーム領域のデバッグ](#Debugging)  
  
-   [フォーム領域の配置](#Deploying)  
  
##  <a name="Enhance"></a> フォーム領域を使用する利点  
 フォーム領域は、従来の Outlook フォーム開発に多くの機能強化をもたらします。  
  
-   標準フォームの既定のページをカスタマイズする。  
  
-   標準フォームに最大 12 ページ追加する。  
  
-   標準フォームを置換または拡張する。  
  
-   閲覧ペインとインスペクターにカスタム UI を表示する。  
  
 詳細については、次を参照してください。[フォーム ページのカスタマイズとフォーム領域](http://msdn.microsoft.com/library/office/ff869060.aspx)です。  
  
##  <a name="Adding"></a> Outlook フォーム領域をプロジェクトに追加します。  
 使用することができます、**新しい Outlook フォーム領域**を新しいフォーム領域をデザインまたは Outlook でデザインしたフォーム領域をインポートするウィザード。 また、別の Outlook VSTO アドイン プロジェクトで使用したフォーム領域がある場合は、既存のフォーム領域を再利用できます。  
  
###  <a name="CreatingFormRegion"></a> ウィザードを使用して新しいフォーム領域の作成  
 フォーム領域を作成するには追加、 **Outlook フォーム領域**項目を Outlook VSTO アドイン プロジェクト。 起動、**新しい Outlook フォーム領域**ウィザード。  
  
 このウィザードでは、新しいフォーム領域をデザインするか、Outlook でデザインしたフォーム領域をインポートするかを指定します。 新しいフォーム領域のデザインの詳細については、次を参照してください。[フォーム領域デザイナーを使用して](#UsingFormRegionDesigner)です。 Outlook でデザインしたフォーム領域の使用に関する詳細については、次を参照してください。 [Outlook でデザインしたフォーム領域をインポートする](#UsingFormRegionDesignedOutlook)です。  
  
 このウィザードでは、作成するフォーム領域の種類を指定します。 フォーム領域の種類について、次の表で説明します。  
  
|領域の種類|説明|  
|-----------------|-----------------|  
|分離|フォーム領域を Outlook フォームの新しいページとして追加します。|  
|隣接|フォーム領域を Outlook フォームの既定のページの下部に追加します。|  
|Replacement|フォーム領域を Outlook フォームの既定のページに代わる新しいページとして追加します。|  
|すべて置換|Outlook フォーム全体をフォーム領域に置き換えます。|  
  
 このウィザードでは、表示条件を指定し、拡張するフォームの種類を選択することもできます。 詳細については、次を参照してください。[する方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)です。  
  
 このウィザードで行った選択は、他のウィザード ページで使用できるオプションに影響します。 例では、選択した場合の**隣接する**または**個別**で、**新しい Outlook フォーム領域を作成** ページで、次に、**タイトル**と**説明**フィールドでは使用できない、**説明のテキストを指定し、表示設定を選択します。**ページ。 これは、隣接または分離フォーム領域を表示するときに、Outlook ではこれらのフィールドを使用しないためです。  
  
#### <a name="form-region-files"></a>フォーム領域ファイル  
 完了すると、**新しい Outlook フォーム領域**ウィザード、Visual Studio が自動的に、次のファイルをプロジェクトに追加します。  
  
-   フォーム領域コード ファイル。 このファイルは、指定した名前、 **Outlook フォーム領域**内の項目、**新しい項目の追加** ダイアログ ボックス。 このファイルには、フォーム領域イベントを処理するコードを追加します。  
  
-   フォーム領域デザイナー コード ファイル。 このファイルは、フォーム領域デザイナーによって生成されたコードを含んでおり、直接編集すべきではありません。  
  
-   Outlook Form Storage (.ofs) ファイル。  
  
    > [!NOTE]  
    >  このファイルがプロジェクトに追加されるのは、Outlook でデザインしたフォーム領域をインポートした場合だけです。  
  
#### <a name="form-region-factory-class"></a>フォーム領域ファクトリ クラス  
 フォーム領域コード ファイルには、<xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> インターフェイスを実装する部分クラスが含まれています。 これがフォーム領域ファクトリ クラスです。 フォーム領域ファクトリ クラスは、フォーム領域の新しいインスタンスを作成するために使用します。  
  
 展開して、このクラスを見つけることができます、**フォーム領域ファクトリ**領域。  
  
 **新しい Outlook フォーム領域**ウィザードでは、このフォーム領域の内部名を指定するクラスとフォーム領域を表示するメッセージ クラスに属性を追加します。 これらの属性は、ファイルがプロジェクトに追加された後、手動で変更できます。  
  
 フォーム領域ファクトリ クラスの大部分は、フォーム領域デザイナー ファイルに実装されます。 ただし、`FormRegionInitializing` イベント ハンドラーはフォーム領域コード ファイルに公開されます。 このイベント ハンドラーを使用して、Outlook がフォーム領域を表示するかどうかを指定できます。 詳細については、次を参照してください。[フォーム領域イベントの処理](#HandlingFormRegionEvents)です。  
  
###  <a name="AddingExistingFormRegion"></a> プロジェクトに既存のフォーム領域を追加します。  
 別の Outlook プロジェクトで使用した Outlook フォーム領域がある場合は、 **[既存項目の追加]** ダイアログ ボックスを使用して、そのフォーム領域を現在の Outlook VSTO アドイン プロジェクトで再利用できます。  
  
 既存のフォーム領域コード ファイル (.vb または .cs) 必要があります。使って Outlook Form Storage (.ofs) ファイルを追加することはできません、**既存項目の追加** ダイアログ ボックス。 ただし、Outlook Form Storage ファイルをインポートすることによって新しいフォーム領域を作成できます。 詳細については、次を参照してください。[する方法: フォーム領域を Outlook アドイン プロジェクトに追加](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)です。  
  
##  <a name="UsingFormRegionDesigner"></a> フォーム領域デザイナーを使用します。  
 フォーム領域デザイナーでは、フォーム領域のレイアウトと外観をデザインできます。 デザイナーの画面にマネージ コントロールをドラッグして、コントロールを開くには、イベント ハンドラーをダブルクリックしておよびでプロパティを設定、**プロパティ**ウィンドウです。  
  
> [!NOTE]  
>  下に Outlook でフォーム領域の表示方法に影響するプロパティを見つけることができます、**マニフェスト**内のノード、**プロパティ**ウィンドウです。  
  
 フォーム領域デザイナーが選択した場合にのみ使用可能な**新しいフォーム領域をデザイン**で、**フォーム領域を作成する方法を選択**のページ、**新しい Outlook フォーム領域**ウィザード。  
  
 フォーム領域デザイナーを開くには、次の 3 つの方法があります。  
  
-   **ソリューション エクスプ ローラー**、フォーム領域コード ファイルをダブルクリックします。  
  
-   **ソリューション エクスプ ローラー**、フォーム領域コード ファイルを右クリックし、クリックして**ビュー デザイナー**です。  
  
-   **ソリューション エクスプ ローラー**、フォーム領域コード ファイルを選択し、[、**ビュー** ] メニューのをクリックして**デザイナー**です。  
  
 フォーム領域デザイナーは、マネージ コントロールのみをサポートしています。 ネイティブな Outlook コントロールを追加することはできません。  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Outlook でデザインしたフォーム領域をインポートします。  
 Outlook でデザインする際に、ネイティブな Outlook コントロールをフォーム領域に追加できます。 ネイティブな Outlook コントロールは、デザイン時に Outlook データにバインドできます。 ただし、その場合はフォーム領域デザイナーを使用してマネージ コントロールを追加したりフォーム領域のデザインを変更したりすることはできません。  
  
 使用して Outlook VSTO アドイン プロジェクトにフォーム領域をインポートすることができます、**新しい Outlook フォーム領域**ウィザード。 **フォーム領域を作成する方法を選択** ページで選択**Outlook Form Storage (.ofs) ファイルをインポート**です。 次に、Outlook Form Storage (.ofs) ファイルの場所を参照します 。 (フォーム領域は .ofs ファイルとして保存されます。)  
  
 **新しい Outlook フォーム領域**ウィザードが .ofs ファイルをプロジェクト ディレクトリにコピーされ、フォーム領域デザイナー ファイルへのコントロールの参照を追加します。 これで、フォーム領域コード ファイルでコントロールのイベントを処理できます。  
  
 Visual Basic プロジェクトでイベントを処理するには、コード エディターの上部にあるメソッド名リストからイベントを選択します。  
  
 C# プロジェクトでイベントを処理するには、<xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> メソッドでコントロール イベントにサブスクライブします。 詳細については、次を参照してください。[する方法: サブスクライブすると、イベント サブスクリプションの解除&#40;C&#35;プログラミング ガイド&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events)です。  
  
 フォーム領域のプロパティは、フォーム領域ファクトリ クラスの `InitializeManifest` メソッドで変更できます。  
  
> [!NOTE]  
>  フォーム領域をインポートするには、開発用コンピューターにインストールされている Outlook と同じバージョンの Outlook を対象とするプロジェクトで作業している必要があります。 たとえば、Outlook 2010 をインストールした場合、フォーム領域でのみ機能プロジェクトのインポートが作成されたを使用して、 **Outlook 2010 アドイン**プロジェクト テンプレート。  
  
### <a name="updating-an-imported-form-regions-design"></a>インポートしたフォーム領域のデザインの更新  
 フォーム領域に対して、コントロールの追加、削除、または変更を行うことができます。 これを行う前に、フォーム領域コード ファイルに追加したコードをバックアップします。 その後、Outlook で .ofs ファイルを開き、フォーム領域を変更し、変更を保存します。 使用して、**新しい Outlook フォーム領域**を変更した .ofs ファイルをインポートするウィザード。 その後、新しいフォーム領域コード ファイルにコードを貼り付けることができます。  
  
##  <a name="AddingCustomCode"></a> フォーム領域へのカスタム コードを追加します。  
 <xref:Microsoft.Office.Tools.Outlook> 名前空間では、フォーム領域、フォーム領域を表示する Outlook アイテム、およびその他の役に立つアイテムを表すクラスにアクセスできます。 **Outlook フォーム領域**項目に自動的にプロジェクトにこのアセンブリへの参照を追加し、挿入、適切な**を使用して**または**Imports**の上部にあるステートメント、フォーム領域コード ファイル。  
  
 ほとんどの Outlook プログラミング タスクを実行するのに Microsoft.Office.Interop.Outlook 名前空間のクラス、メソッド、およびプロパティを使用できます。 Outlook オブジェクト モデルの詳細については、次を参照してください。 [Outlook オブジェクト モデルの概要](../vsto/outlook-object-model-overview.md)です。 Outlook オブジェクト モデルを使用し、表示する一般的なタスクの例については[Outlook ソリューション](../vsto/outlook-solutions.md)です。  
  
###  <a name="HandlingFormRegionEvents"></a> フォーム領域イベントの処理  
 **Outlook フォーム領域**アイテム フォーム領域コード ファイルに次の 3 つのイベント ハンドラーを自動的に追加します。  
  
|event|説明|  
|-----------|-----------------|  
|FormRegionInitializing|フォーム領域が初期化される前に発生します。 このイベント ハンドラーの状態をチェックして、Outlook がフォーム領域を表示する必要があるかどうかを判定できます。 詳細については、次を参照してください。[する方法: フォーム領域が表示されないようにする Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)です。|  
|FormRegionShowing|フォーム領域のインスタンスが作成されてから、フォーム領域が表示される前までの間に発生します。|  
|FormRegionClosed|フォーム領域が閉じられる前に発生します。|  
  
##  <a name="Building"></a> プロジェクトのビルド  
 フォーム領域を含む Outlook VSTO アドイン プロジェクトをビルドすると、Visual Studio によってレジストリに次の情報が追加されます。  
  
-   1 つ以上のフォーム領域に関連付けられている各メッセージ クラスのキー。  
  
-   各フォーム領域のエントリと、Outlook VSTO アドインの名前を表す関連値。  
  
 この情報は、Outlook がフォーム領域を読み込むときに使用されます。  
  
##  <a name="Debugging"></a> フォーム領域のデバッグ  
 フォーム領域を含む Outlook VSTO アドインは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトと同じようにデバッグできます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを起動すると、Visual Studio によって自動的に Outlook が起動されます。  
  
 フォーム領域を表示するには、対応する Outlook アイテムを開く必要があります。 たとえば、隣接フォーム領域をメール アイテムの下部に追加する場合は、メール アイテムを開きます。  
  
##  <a name="Deploying"></a> フォーム領域の配置  
 フォーム領域は、関連付けられた Outlook VSTO アドインと共に自動的に配置されます。 したがって、フォーム領域を配置するための特別なタスクを実行する必要はありません。 詳細については、VSTO アドインの配置は、次を参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Outlook フォーム領域の作成に関するガイドライン](../vsto/guidelines-for-creating-outlook-form-regions.md)|フォーム領域を最適化し、発生する可能性のある問題を回避するのに役立つ情報を提供します。|  
|[方法: フォーム領域を Outlook アドイン プロジェクトに追加する](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|使用して標準またはカスタムの Microsoft Office Outlook フォームを拡張するフォーム領域を作成する方法を示します、**新しい Outlook フォーム領域**ウィザード。|  
|[フォーム領域の Outlook メッセージ クラスへの関連付け](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|フォーム領域を各アイテムのメッセージ クラスに関連付けることにより、そのフォーム領域を表示する Microsoft Office Outlook アイテムを指定する方法について説明します。|  
|[チュートリアル: Outlook フォーム領域のデザイン](../vsto/walkthrough-designing-an-outlook-form-region.md)|連絡先アイテムのインスペクター ウィンドウに新しいページとして表示するカスタム フォーム領域をデザインする方法について説明します。|  
|[チュートリアル: Outlook でデザインしたフォーム領域のインポート](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Microsoft Office Outlook でフォーム領域をデザインしを使用して Outlook VSTO アドイン プロジェクトにフォーム領域をインポートする方法を示します、**新しい Outlook フォーム領域**ウィザード。|  
|[実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)|コードを記述して、フォーム領域でコントロールの表示、非表示、変更を行う方法と、`Globals` クラスを使用して、記述したコードをユーザーがプロジェクト内の他の領域から実行できるようにする方法について説明します。|  
|[方法: Outlook にフォーム領域が表示されないようにする](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Microsoft Office Outlook で特定のアイテムのフォーム領域が表示されないようにする方法について説明します。|  
|フォーム領域が表示される Outlook アイテムにアクセスする方法について説明します。|  
|[Outlook フォーム領域のカスタム動作](../vsto/custom-actions-in-outlook-form-regions.md)|ユーザーが Outlook アイテムに応答できるようにする方法について説明します。|  
  
  