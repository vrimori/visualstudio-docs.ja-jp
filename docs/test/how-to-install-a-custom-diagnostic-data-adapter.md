---
title: '方法: Visual Studio でカスタム診断データ アダプターをインストールする'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 0755f77b2eea2860a3514480504c7aed041711d4
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379290"
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>方法: カスタム診断データ アダプターをインストールする

カスタム診断データ アダプターを作成した場合、または使用するカスタム診断データ アダプターを提供された場合は、診断データ アダプターのアセンブリ ファイルをローカル コンピューターの適切なディレクトリにコピーすることにより、診断データ アダプターのアセンブリをインストールできます。

 環境に含まれているロールでカスタム診断データ アダプターを使用する場合は、そのロールで使用できるテスト エージェントが実行されるすべてのコンピューターにその診断データ アダプターをインストールする必要があります。

 次の手順に従って、カスタム診断アダプターを適切な場所にインストールします。 診断データ アダプターをインストールするコンピューターの管理アクセス許可が必要です。

## <a name="install-a-custom-diagnostic-data-adapter"></a>カスタム診断データ アダプターをインストールする

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>カスタム診断データ アダプターをインストールするには

1.  クライアント コンピューターまたはエージェント コンピューターでテストを実行するときに診断データ アダプターを使用するには、すべてのファイルをビルド ディレクトリからターゲット コンピューターにコピーします。コピー先は、インストール パスに基づく以下のディレクトリです。

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     コピーするファイルは次のとおりです。

    -   診断データ アダプターのアセンブリ (*.dll*) (必須)。

    -   アダプターのデバッグ データ ファイル (*.pdb*) (省略可能)。

    -   既定の構成設定がある場合は、アダプターの構成ファイル (`<diagnostic data adapter name>.dll.config`) (省略可能)。

    -   アダプターの構成設定を編集するために作成した場合は、構成エディターのアセンブリ (省略可能)。 これはクライアント コンピューターの場合のみです。 エージェント コンピューターではエディターを使用しません。

    > [!NOTE]
    > 診断データ アダプターと構成エディターを同じプロジェクトで作成し、同じアセンブリに組み込むこともできますが、個別のプロジェクトを使用して、個別のアセンブリを作成することもできます。

     テストの実行時に環境を使用するようにテストの設定を構成する方法の詳細については、[手動テストで診断データを収集する方法 (VSTS) ](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)に関するページを参照してください。

2.  テストの診断データ アダプターを選択するには、まず、既存のテスト設定を選択するか、Microsoft Test Manager または Visual Studio で新しいテスト設定を作成してから、選択したテスト設定の **[データと診断]** タブで診断データ アダプターを選択する必要があります。

3.  診断データ アダプター構成エディターを作成およびインストールした場合、テスト設定用の診断データ アダプターを構成するには、アダプター名の横の **[構成]** をクリックし、必要な変更を行います。 **[保存]** を選択します。 診断データ コレクターの構成エディターを作成する方法については、「[方法: 診断データ アダプター用のデータのカスタム エディターを作成する](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)」を参照してください。

4.  Microsoft Test Manager からテストを実行する場合は、テストを実行する前にこれらのテストの設定をテスト計画に割り当てるか、**[オプションを指定して実行]** コマンドを使用して、テストの設定の割り当ておよびオーバーライドを行います。 テスト設定の詳細については、「[テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)」を参照してください。

     Visual Studio からテストを実行する場合は、これらのテスト設定をアクティブとして設定する必要があります。 テスト設定の詳細については、「[テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)」を参照してください。

5.  選択した診断データ アダプターを指定したテストの設定を使用して、テストを実行します。

## <a name="see-also"></a>関連項目

- [方法: 診断データ アダプターを作成する](../test/how-to-create-a-diagnostic-data-adapter.md)
- [方法: 診断データ アダプター用のデータのカスタム エディターを作成する](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [診断データ アダプター作成用のサンプル プロジェクト](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [診断データ アダプターを作成してカスタム データを収集する、またはテスト コンピューターに影響を与える](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)