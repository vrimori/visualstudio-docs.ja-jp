---
title: Office ソリューションを構築します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4adafc1acfda949a16a3daa3db8da2e96eba2d0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="build-office-solutions"></a>Office ソリューションを構築します。
  一般に、Office プロジェクトのビルドとデバッグは、Visual Studio のその他の種類のプロジェクト (Windows フォームなど) のビルドおよびデバッグとほとんど同じです。 このセクションのトピックでは、いくつかある相違点について説明します。 アプリケーションを構築する方法についての概要については、次を参照してください。[コンパイルし、Visual Studio で構築](/visualstudio/ide/compiling-and-building-in-visual-studio)です。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="project-output-for-office-projects"></a>Office プロジェクトのプロジェクト出力  
 Office プロジェクトは、 *プロジェクト名*\bin\release または *プロジェクト名*\bin\debug に出力されます。 配置ディレクトリにはビルドできません。  
  
### <a name="document-level-projects"></a>ドキュメント レベルのプロジェクト  
 ドキュメント レベルのプロジェクトをビルドすると、プロジェクト出力には次の項目が含まれるようになります。  
  
-   プロジェクト ドキュメントのコピー。  
  
-   プロジェクト アセンブリと、 **［ローカル コピー］** プロパティが **true**に設定されているすべての参照先アセンブリ。  
  
-   ファイル名拡張子を持つアプリケーション マニフェスト *.manifest*です。 詳細については、次を参照してください。 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
-   配置マニフェストは、ファイル名拡張子を持つ *.vsto*です。 詳細については、次を参照してください。 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)です。  
  
-   プログラム データベース (*PDB*) ファイル。  
  
> [!NOTE]  
>  ドキュメント レベルのソリューションを、ローカル コンピューターではなくリモートの場所に作成する場合は、アプリケーションのセキュリティ センターにある信頼できる場所のリストに完全修飾パスを追加します。 詳細については、ドキュメントへの信頼の付与と呼ばれるセクションを参照してください。[セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)です。  
  
### <a name="application-level-projects"></a>アプリケーション レベルのプロジェクト  
 VSTO アドイン プロジェクトをビルドすると、次の項目がプロジェクト出力に含まれます。  
  
-   プロジェクト アセンブリと、 **［ローカル コピー］** プロパティが **true**に設定されているすべての参照先アセンブリ。  
  
-   ファイル名拡張子を持つアプリケーション マニフェスト *.manifest*です。 詳細については、次を参照してください。 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)です。  
  
-   配置マニフェストは、ファイル名拡張子を持つ *.vsto*です。 詳細については、次を参照してください。 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)です。  
  
-   プログラム データベース (*PDB*) プロジェクト アセンブリのファイルです。  
  
 VSTO アドイン プロジェクトのビルド処理により、開発用コンピューターには、VSTO アドインの読み込みに必要な一連のレジストリ エントリも作成されます。 詳細については、次を参照してください。 [VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)です。  
  
 フォーム領域を含む Outlook VSTO アドイン プロジェクトをビルドすると、ビルド処理により、次に示す情報がレジストリに追加されます。  
  
-   1 つ以上のフォーム領域に関連付けられている各メッセージ クラスのキー。  
  
-   各フォーム領域のエントリと、Outlook VSTO アドインの名前を表す関連値。  
  
 この情報は、Outlook がフォーム領域を読み込むために必要になります。  
  
## <a name="referenced-assemblies"></a>参照アセンブリ  
 Office ソリューションのビルド プロジェクトからアセンブリ (クラス ライブラリ プロジェクトを含む) を参照できます。 各参照先アセンブリには、 **［ローカル コピー］** というプロパティがあります。 **［ローカル コピー］** では、アセンブリを出力ディレクトリにコピーするかどうかを指定します。 既定では **true**に設定されています。 **［ローカル コピー］** が **true** に設定されている参照先アセンブリは、すべて出力ディレクトリにコピーされます。  
  
## <a name="security-during-the-build-process"></a>ビルド プロセス中のセキュリティ  
 ビルド処理中、Visual Studio は、ソリューションに信頼を付与するように、開発用コンピューター上のセキュリティ設定を自動的に構成します。 これにより、デバッグしながらソリューションを実行できるようになります。  
  
 Office プロジェクトでは、発行者を確認するために証明書が使用されます。 Visual Studio は、Office ソリューションを識別するための一時的な証明書を自動的に作成し、その一時的な証明書を信頼するように開発コンピューターを構成します。  
  
 詳細については、次を参照してください。[セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)です。  
  
### <a name="network-projects"></a>ネットワーク プロジェクト  
 アセンブリまたはドキュメントの場所がネットワーク共有上に存在している場合は、ローカル (User レベル) セキュリティ ポリシーを更新するだけでは、ソリューションを実行できるようになりません。 管理者は、ソリューションの実行前に、コンピューター (Machine) レベルで、ネットワーク共有上のアセンブリとドキュメントに完全な信頼を付与する必要があります。 セキュリティ ポリシーを設定する方法の詳細については、次を参照してください。[セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)です。  
  
 ドキュメント レベルのプロジェクトでは、Office の信頼できるフォルダーのリストに、ドキュメントの完全修飾位置を追加する必要もあります。 詳細については、次を参照してください。[ドキュメントへの信頼を付与](../vsto/granting-trust-to-documents.md)です。  
  
## <a name="change-the-platform-target"></a>プラットフォーム ターゲットを変更します。  
 既定では、Office プロジェクトのプラットフォーム ターゲットは **Any CPU**です。 通常、この設定を変更する必要はありません。 **Any CPU** プラットフォーム ターゲット設定でビルドされた Officeソリューションは、32 ビット バージョンと 64 ビット バージョンの Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] または [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]で実行するようになります。  
  
 64 ビット バージョンの Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] または [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]でのみ実行するソリューションを作成していて、そのソリューションからネイティブの 64 ビット API を呼び出す場合は、プラットフォーム ターゲットを x64 に限定して設定する必要があります。 プラットフォーム ターゲット設定の変更の詳細については、次を参照してください。[する方法: プロジェクトのターゲット プラットフォームを](../ide/how-to-configure-projects-to-target-platforms.md)です。  
  
 プラットフォーム ターゲットを x64 に設定すると、そのソリューションは 32 ビット バージョンの Windows または Office では実行できなくなります。 x64 プラットフォーム ターゲットには、64 ビット プロセスで実行するソリューションが必要になります。  
  
## <a name="use-the-clean-command"></a>[クリーン] コマンドを使用します。  
 開発用コンピューターからビルド済みのプロジェクト ファイルを削除する場合は、 **の** [ビルド] **メニューにある** [クリーン] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]コマンドを使用できます。 **[クリーン]** コマンドにより、ビルドの出力場所にあるファイルがすべて削除されます。 アプリケーション レベルのプロジェクトの場合は、 **[クリーン]** コマンドによって、ビルド処理で作成されたレジストリ エントリも削除されます。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Office プロジェクトをデバッグします。](../vsto/debugging-office-projects.md)|Office プロジェクトのデバッグに関する問題について説明します。|  
|[チュートリアル: 初めての Excel 用ドキュメント レベルのカスタマイズを作成します。](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel 用の基本的なドキュメント レベルのカスタマイズを作成する方法を示します。|  
|[方法: 無効になっている VSTO アドインで再度有効にします。](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|ハードまたはソフトに無効化されている VSTO アドインを再度有効化する方法について説明します。|  
|[設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)|Office ソリューションの作成に関する情報と、ソリューション内のアセンブリの役割に関する情報へのリンクが掲載されています。|  
  
  