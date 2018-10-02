---
title: Visual Studio のアンインストール |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c5a0ea6083a5b65f7bab667394a42900089d21ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548802"
---
# <a name="uninstall-visual-studio"></a>Visual Studio のアンインストール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [Visual Studio 2017 のアンインストール](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio)します。

このページには、Visual Studio 2015、以前のバージョンの開発者向け生産性向上ツールの統合されたスイートのアンインストールをについて説明します。  
  
##  <a name="uninstalling"></a>   
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>"Standard"のアンインストール方法を使用して Visual Studio をアンインストールするには  
  
1.  **コントロール パネルの [** の**プログラムと機能**] ページで、アンインストール、および選択する製品のエディション**変更**します。  
  
2.  セットアップ ウィザードで選択**アンインストール**、選択**はい**、ウィザードの残りの指示に従います。  
  
 この standard、または既定の方法はいくつか残ります installation of Visual Studio をインストール (たとえば、Microsoft .NET Framework、Microsoft Visual C++ 再頒布可能パッケージ、Microsoft SQL Server など) の背後にある項目。   これらの他の多くのアプリケーションがそれらに依存するためにインストールされているままにします。 ただし、これらも削除する場合は、選択内のエントリ**プログラムと機能**、し、それぞれを個別に削除します。  
  
#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Visual Studio および他のすべての関連ファイルをアンインストールする (つまり、ほぼすべてをアンインストールする)  
  
1.  Visual Studio の .exe ファイルを見つけます (たとえば、"vs_enterprise.exe"を検索します)。  
  
    > [!NOTE]
    >  ファイルは、例の"%ProgramData%\Package Cache"のサブフォルダーである必要があります: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe  
  
2.  使用して .exe ファイルを実行、/uninstall/force コマンド ライン パラメーターです。  
  
     たとえば、実行```vs_enterprise.exe /uninstall /force```、Visual Studio およびは残されるコア コンポーネントのほとんどは、既定のアンインストールで削除するされます。 ただし、これは削除されません追加コンテンツのすべての Visual Studio のアドオンと (例、Visual Studio の更新プログラム、およびその他のオプションのコンポーネント) の拡張機能をインストールできます。  
  
    > [!TIP]
    > また、使用することができます、"**合計アンインストーラー**"Visual Studio ですべて削除するツールまたは Visual Studio の更新プログラムをインストールした可能性があります。 つまり、任意のバージョンの Visual Studio 2013 またはそれ以降。 詳細については、次を参照してください。、 [Visual Studio アンインストーラー ツール](https://github.com/Microsoft/VisualStudioUninstaller/releases)GitHub でします。  
  
#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>サイレント モードまたはパッシブ モードで Visual Studio をアンインストールする (つまり、ソースからアンインストールする)  
  
1.  Visual Studio がインストールされているコンピューターで、Windows コマンド プロンプトを開きます。  
  
2.  次のパラメーターを入力します。  
  
     *DVDRoot* \\< インストール ファイル\> \</quiet&#124;/passive > [/norestart]/uninstall  
  
#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>以前のバージョンまたはリリースの Visual Studio にロールバックするには  
  
1.  このトピックに記載する方法のいずれかを使用して Visual Studio をアンインストールします。  
  
    > [!WARNING]
    >  期待どおりに Visual Studio (または Visual Studio の更新) の現在のリリースをアンインストールし、以前のリリースをインストールが動作しない可能性があります。  
    >   
    >  結果によって異なりますバージョンまたは Visual Studio のインストールがある場合は、そのコンポーネントのバージョンがインストールされている場合、どの製品がインストールされている Visual Studio のリリースまたはそのコンポーネントでは、依存関係をする必要があり、最後でのリリースインストールまたは再インストールを計画するどの Visual Studio の以前のバージョン。  これらすべての変数のため標準的なアンインストールは多くの場合、コンポーネントのままには、Visual Studio の以前のバージョンまたはリリースでは動作しません。  
    >   
    >  そのため、最良の結果をお勧めしますを使用して、 [Visual Studio アンインストーラー ツール](https://github.com/Microsoft/VisualStudioUninstaller/releases)します。  
  
2.  使用する Visual Studio の以前のバージョンをインストールまたは再インストールします。  
  
 Visual Studio の以前のバージョンをインストールする場合でも、新しいバージョンを使用して、またはリリースがある場合にお試しくださいまだセットアップ プログラム可能性があります。 詳細についてを参照してください、[方法: 特定のリリースの Visual Studio をインストール](../install/how-to-install-a-specific-release-of-visual-studio.md)トピック。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のインストール](https://msdn.microsoft.com/library/e2h7fzkw.aspx)