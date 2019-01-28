---
title: ドキュメント レベルのカスタマイズのアーキテクチャ
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e80fbe0244c897f626c6fba248447881a92594a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868457"
---
# <a name="architecture-of-document-level-customizations"></a>ドキュメント レベルのカスタマイズのアーキテクチャ
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Word および Microsoft Office Excel のドキュメント レベルのカスタマイズを作成するためのプロジェクトが含まれています。 ここでは、ドキュメント レベルのカスタマイズの次の側面について説明します。  
  
- [カスタマイズを理解します。](#UnderstandingCustomizations)  
  
- [カスタマイズのコンポーネント](#Components)  
  
- [カスタマイズと Microsoft Office アプリケーションの連携](#HowCustomizationsWork)  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  ドキュメント レベルのカスタマイズを作成する方法の概要については、次を参照してください[Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)、 [Word用ドキュメントレベルカスタマイズのプログラミングを開始します。](../vsto/getting-started-programming-document-level-customizations-for-word.md)、および[Excel のドキュメント レベルのカスタマイズのプログラミングを始める](../vsto/getting-started-programming-document-level-customizations-for-excel.md)します。  
  
##  <a name="UnderstandingCustomizations"></a> カスタマイズを理解します。  
 Visual Studio の Office 開発ツールを使用してドキュメント レベルのカスタマイズをビルドする場合は、特定の文書に関連付けられたマネージド コード アセンブリを作成します。 アセンブリがリンクされている文書やブックは、マネージド コード拡張機能がある、と言い表されます。 詳細については、次を参照してください。[デザイン Office ソリューションの作成と](../vsto/designing-and-creating-office-solutions.md)します。  
  
 ユーザーがドキュメントを開くと、Microsoft Office アプリケーションによってアセンブリが読み込まれます。 アセンブリが読み込まれると、ドキュメントが開いている間、カスタマイズはイベントに応答できます。 また、ドキュメントが開いている間、カスタマイズはオブジェクト モデルを呼び出し、アプリケーションを自動化して拡張することもできます。 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]内の任意のクラスを使用することも可能です。  
  
 アセンブリは、アプリケーションのプライマリ相互運用機能アセンブリを介してアプリケーションの COM コンポーネントとの通信を行います。 詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)と[Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)します。  
  
 複数のドキュメント レベルのカスタマイズを同時に開くと、各アセンブリは異なるアプリケーション ドメインに読み込まれます。 このため、1 つのソリューションが正しく動作しない場合でも、それが原因で他のソリューションにエラーが発生することはありません。 ドキュメント レベルのカスタマイズは、1 つのアプリケーション ドメイン内の 1 つのドキュメントと連携するように設計されています。 ドキュメント間のやり取りに対応するようには設計されていません。 アプリケーション ドメインの詳細については、次を参照してください。[アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)します。  
  
> [!NOTE]  
>  Visual Studio の Office 開発ツールを使用して作成するドキュメント レベルのカスタマイズは、エンド ユーザーがアプリケーションを起動したときのみ使用されることを目的としています。 アプリケーションがプログラムで起動された場合 (オートメーション機能を使用する場合など)、カスタマイズは予期したとおりに動作しないことがあります。  
  
### <a name="design-time-and-run-time-experiences"></a>デザイン時と実行時のエクスペリエンス  
 ドキュメント レベルのカスタマイズのアーキテクチャを理解すると、ソリューションのデザイン時と実行時におけるエクスペリエンスについて理解を深めることができます。  
  
#### <a name="design-time"></a>デザイン時  
 デザイン時のエクスペリエンスには、次のような手順が含まれます。  
  
1.  開発者は、ドキュメント レベルのプロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で作成します。 このプロジェクトには、ドキュメントと、ドキュメントとは分離して実行されるアセンブリが組み込まれます。 ドキュメントが既に存在する (デザイナーで作成した)、または、プロジェクトと共に新しいドキュメントを作成することができます。  
  
2.  設計者 (プロジェクトを作成する開発者、または他のユーザーのいずれか) は、エンド ユーザー向けにドキュメントの最終的な外観を仕上げます。  
  
#### <a name="runtime"></a>ランタイム  
 実行時のエクスペリエンスには、次のような手順が含まれます。  
  
1.  エンド ユーザーが、マネージド コード拡張機能を実装している文書またはブックを開きます。  
  
2.  文書またはブックにより、コンパイルされたアセンブリが読み込まれます。  
  
3.  ユーザーが文書またはブックで操作すると、アセンブリがイベントに応答します。  
  
#### <a name="developer-and-end-user-perspective-compared"></a>開発者とエンドユーザーの立場の違い  
 開発者は主に [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]で作業を行い、エンド ユーザーは Word または Excel で作業を行うため、ドキュメント レベルのカスタマイズを理解するには、次に示す 2 つの視点に立つことが必要です。  
  
|開発者の視点|エンド ユーザーの視点|  
|-----------------------------|----------------------------|  
|開発者は [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を使用して、Word および Excel にアクセス可能なコードを記述します。<br /><br /> Word または Excel を実行する実行可能ファイルを作成しているように思えますが、実際の処理は別の方法で行われます。 ドキュメントにはアセンブリが関連付けられており、そのアセンブリへのポインターが含まれています。 ドキュメントを開くと、Word または Excel はアセンブリを検索し、すべてのイベント処理に呼応して動作します。|ソリューションを使用するには、他の Microsoft Office ファイルを開く場合と同様に、文書またはブックを開く (または、テンプレートから新しいドキュメントを作成する) だけです。<br /><br /> アセンブリにより、文書またはブックをカスタマイズできます。たとえば、現在のデータを基に文書やブックを自動生成したり、情報の入力を求めるダイアログ ボックスを表示したりできます。|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>ドキュメント レベルのカスタマイズのドキュメント形式をサポート  
 カスタマイズ プロジェクトを作成するときには、プロジェクト内で使用するドキュメントの形式を選択できます。 詳細については、「[方法 :Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)です。  
  
 Excel および Word のドキュメント レベルのカスタマイズで使用可能なドキュメント形式を、次の表に示します。  
  
|Excel|Word|  
|-----------|----------|  
|Excel ブック (*.xlsx*)<br /><br /> Excel マクロ有効ブック (*.xlsm*)<br /><br /> Excel バイナリ ブック (*.xlsb*)<br /><br /> Excel 97-2003 ブック (*.xls*)<br /><br /> Excel テンプレート (*.xltx*)<br /><br /> Excel マクロ有効テンプレート (*.xltm*)<br /><br /> Excel 97-2003 テンプレート (*.xlt*)|Word 文書 (*.docx*)<br /><br /> Word マクロ有効文書 (*.docm*)<br /><br /> Word 97-2003 文書 (*.doc*)<br /><br /> Word テンプレート (*.dotx*)<br /><br /> Word マクロ有効テンプレート (*.dotm*)<br /><br /> Word 97-2003 テンプレート (*.dot*)|  
  
 サポートされている形式のドキュメントに対してだけ、マネージド コード拡張機能を設計する必要があります。 そうしないと、アプリケーションでドキュメントを開くときに、特定のイベントが発生しない可能性があります。 たとえば、 <xref:Microsoft.Office.Tools.Excel.Workbook.Open> Excel XML スプレッドシート形式または web ページに保存するブックでマネージ コード拡張機能を使用すると、イベントは発生しません (*.htm*;*.html*) 形式。  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>.Xml ファイル名拡張子を持つ Word 文書のサポート  
 ドキュメント レベルのプロジェクト テンプレートを使用して、次のファイル形式に基づくプロジェクトを作成することはできません。  
  
- Word XML 文書 (*\*xml*)。  
  
- Word 2003 XML 文書 (*\*xml*)。  
  
  エンド ユーザーがこれらのファイル形式でカスタマイズを使用できるようにするには、前の表に示した、サポートされているいずれかのファイル形式に基づくカスタマイズを作成して配置します。 カスタマイズをインストールすると、エンドユーザーは、Word XML ドキュメントのドキュメントを保存できます (*\*xml*) 形式または Word 2003 XML 文書 (*\*xml*) 形式、およびカスタマイズは引き続き期待どおりに動作します。  
  
##  <a name="Components"></a> カスタマイズのコンポーネント  
 カスタマイズの主要なコンポーネントは、ドキュメントとアセンブリです。 これらのコンポーネントに加えて、Microsoft Office アプリケーションがカスタマイズを検出して読み込むときに重要な役割を果たすものがあります。  
  
### <a name="deployment-manifest-and-application-manifest"></a>配置マニフェストとアプリケーション マニフェスト  
 カスタマイズは、配置マニフェストとアプリケーション マニフェストを使用して、最新バージョンのカスタマイズ アセンブリを特定し、読み込みます。 配置マニフェストは、最新のアプリケーション マニフェストを指します。 アプリケーション マニフェストは、カスタマイズ アセンブリを指し、エントリ ポイント クラス (1 つまたは複数のクラス) を指定して、アセンブリ内で実行します。 詳細については、次を参照してください。 [Office ソリューションでのアプリケーションと展開マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)します。  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office ランタイム  
 Visual Studio での Office developer tools を使用して作成されたドキュメント レベルのカスタマイズを実行するエンドユーザーのコンピューターがいる必要があります、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]をインストールします。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] には、カスタマイズ アセンブリを読み込むアンマネージド コンポーネントが含まれています。また、一連のマネージド アセンブリも含まれています。 これらのマネージド アセンブリにより、カスタマイズ コードがホスト アプリケーションを自動化して拡張するために使用するオブジェクト モデルが提供されます。  
  
 詳細については、次を参照してください。 [Visual Studio tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)します。  
  
##  <a name="HowCustomizationsWork"></a> Microsoft Office アプリケーションとカスタマイズのしくみ  
 ユーザーが Microsoft Office カスタマイズの一部であるドキュメントを開くと、アプリケーションはそのドキュメントにリンクされている配置マニフェストを使用して、最新バージョンのカスタマイズ アセンブリを特定し、読み込みます。 配置マニフェストの場所がという名前のカスタム ドキュメント プロパティに格納されている**AssemblyLocation**します。 この場所を示す文字列は、ソリューションをビルドするときにプロパティに挿入されます。  
  
 配置マニフェストはアプリケーション マニフェストを指し、アプリケーション マニフェストは最新のアセンブリを指します。 詳細については、次を参照してください。 [Office ソリューションでのアプリケーションと展開マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)します。  
  
 ドキュメント レベルのカスタマイズに関する基本アーキテクチャを、次の図に示します。  
  
 ![2007 office カスタマイズ アーキテクチャ](../vsto/media/office07-custom.png "2007 Office カスタマイズ アーキテクチャ")  
  
> [!NOTE]  
>  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]を対象とする Office ソリューションでは、ソリューションはプライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) を直接呼び出す代わりに、ソリューション アセンブリに埋め込まれた PIA 型情報を使用してホスト アプリケーションのオブジェクト モデルを呼び出します。 詳細については、次を参照してください。[デザイン Office ソリューションの作成と](../vsto/designing-and-creating-office-solutions.md)します。  
  
### <a name="loading-process"></a>読み込みプロセス  
 ユーザーが Microsoft Office ソリューションの一部であるドキュメントを開くと、次の処理が実行されます。  
  
1.  Microsoft Office アプリケーションはカスタム ドキュメント プロパティをチェックして、そのドキュメントに関連付けられているマネージド コード拡張機能があるかどうかを調べます。 詳細については、次を参照してください。[カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)します。  
  
2.  マネージ コード拡張機能がある場合は、アプリケーションの読み込み*VSTOEE.dll*、どのロード*VSTOLoader.dll*します。 これらは管理対象ではありませんが、Visual Studio 2010 Tools for Office runtime のローダー コンポーネント Dll。 詳細については、次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)します。  
  
3.  *VSTOLoader.dll*読み込みます、[!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]のマネージ部分を起動し、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。  
  
4.  ドキュメントがローカル コンピューター以外の場所から開かれている場合、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、該当する Office アプリケーション用に設定された **[セキュリティ センターの設定]** の **[信頼できる場所]** の一覧にドキュメントの場所が載っていることを確認します。 ドキュメントの場所が信頼できる場所でない場合、カスタマイズは信頼されず、読み込みプロセスはここで停止します。  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、ソリューションをインストールし (まだインストールされていない場合)、最新のアプリケーション マニフェストと配置マニフェストをダウンロードし、一連のセキュリティ チェックを実行します。 詳細については、次を参照してください。[セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)します。  
  
6.  カスタマイズを信頼して実行できる場合、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は配置マニフェストとアプリケーション マニフェストを使用して、アセンブリの更新をチェックします。 利用できる新しいバージョンのアセンブリが存在する場合、ランタイムは、クライアント コンピューターの [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] キャッシュに新しいバージョンのアセンブリをダウンロードします。 詳細については、次を参照してください。 [Office ソリューションを配置](../vsto/deploying-an-office-solution.md)します。  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、カスタマイズ アセンブリを読み込むときに使用する、新しいアプリケーション ドメインを作成します。  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、カスタマイズ アセンブリをアプリケーション ドメインに読み込みます。  
  
9.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は、カスタマイズ アセンブリ内の **Startup** イベント ハンドラーを呼び出します。 詳細については、次を参照してください[Office プロジェクト内のイベント。](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [カスタム ドキュメント プロパティの概要](../vsto/custom-document-properties-overview.md)   
 [ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)  
