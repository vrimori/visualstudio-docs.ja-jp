---
title: "Visual Studio 2010 単体テスト プロジェクトをアップグレードする | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: mlearned
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: dac3cb1d7767c2ff76ac25f6a486ad30a8d54831
ms.openlocfilehash: 806f5004a4ab3d33d4be86cd4784de989c5fd282
ms.lasthandoff: 03/03/2017

---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Visual Studio 2010 単体テスト プロジェクトをアップグレードする
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] には [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 テスト プロジェクトとの、テスト プロジェクト互換性があります。 たとえば、[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 を使用して作成したテスト プロジェクトを、アップグレードせずに [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] で開くことができます。 したがって、チームは同じテスト プロジェクトの作業に [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 と [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] の両方を使用できます。 詳しくは、「[Visual Studio 2010 からアップグレードをテストできます](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)」を参照してください。  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] には単体テストのいくつかの変更が加わります。 これらの変更のため、Visual Studio の以前のバージョンと [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 間の互換性の問題について理解することは重要です。 単体テストの変更の中でも重要な変更は、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] に単体テスト プロジェクト テンプレートをはじめ、複数のテスト プロジェクト テンプレートが含まれることです。 新しい単体テストは、新しい単体テスト プロジェクト テンプレートに追加されます。 単体テストはまた、コード化された UI テスト プロジェクト テンプレートと呼ばれる別の新しいテスト プロジェクト テンプレートに含めることもできます。 新しいテスト プロジェクト テンプレートの詳細については、「[旧バージョンの Visual Studio からのテストのアップグレード](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)」を参照してください。 既定では、新しい単体テスト プロジェクトにテスト設定ファイルは含まれなくなりました。 テスト設定ファイルを除外すると、単体テストのパフォーマンスが向上します。 互換性については、Visual Studio 2010 を使用して作成した既存のテスト プロジェクトを引き続き使用できます。 しかし、テスト設定ファイルの具体的な必要性がないのであれば、パフォーマンス上の理由から、テスト プロジェクトに関連付けられているテスト設定ファイルを削除することをお勧めします。 たとえば、分散環境で単体テストを実行したり、特定の診断データを収集する必要があったりする場合、テスト設定ファイルを保持することもできます。 同様に、新しい単体テスト プロジェクト テンプレートや、コード化された UI テスト プロジェクト テンプレートを使用する必要がある場合、テスト設定ファイルを手動で追加することもできます。  
  
> [!NOTE]
>  既存の [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 テスト プロジェクトの単体テストは、[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 と [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] の間でシームレスに機能します。 単体テストを含む Visual Studio 2010 テスト プロジェクトを [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] で開いた場合、またはその逆の場合、テスト プロジェクト ファイルは変更されません。  
  
> [!CAUTION]
>  Visual Studio 2010 は 11.0 ツールセットを対象とした C++/CLI プロジェクト、つまり Visual Studio 2012 で作成されたプロジェクトを開くことはできません。 この制限は、C++/CLI 単体テスト プロジェクトのみならず、すべての C++/CLI プロジェクトに適用されます。  
  
> [!NOTE]
>  コマンド ラインから vstest.console.exe を使用して新しい単体テストを実行できます。 vstest.console.exe 使用の詳細については、「[VSTest.Console.exe のコマンド ライン オプション](/devops-test-docs/test/vstest-console-exe-command-line-options)」を参照するか、ヘルプ スイッチ **vstest.console.exe /?** を使用してコマンドを実行してください。 MStest.exe を使用して既存の単体テストの実行を継続できます。 詳細については、「[MSTest を使用したコマンド ラインからの自動テストの実行](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)」および「[MSTest.exe のコマンド ライン オプション](/devops-test-docs/test/mstest-exe-command-line-options)」を参照してください。  
  
 もう&1; つの重要な変更は、新しいテスト エクスプローラーです。 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] では、Visual Studio の以前のバージョンで使い慣れていたかもしれない、テスト ビュー ウィンドウのような、いくつかのテスト用ウィンドウが使用されなくなっています。 テスト エクスプローラーは、ソフトウェア開発作業に単体テストを導入した開発者や開発チームをよりよくサポートするように設計されています。 詳細については、「[テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)」を参照してください。  
  
## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Visual Studio 2010 SP1 と Visual Studio 2012 の互換性の問題  
 Visual Studio 2010 SP1 と [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] の間で単体テストを移行する場合に、知っておくべきいくつかの問題があります。  
  
|単体テスト機能|懸案事項|ソリューション|  
|-----------------------------|-----------|--------------|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] では、テスト リスト (.vsmdi ファイル) は使用されていません。|Visual Studio から新しいテスト リスト (.vsmdi ファイル) を作成、またはテスト リストを実行することはできません。 **ヒント:** テスト カテゴリは、旧バージョンの Microsoft Visual Studio のテスト リスト機能よりも高い柔軟性を備えています。 テスト カテゴリと論理演算子を組み合わせて使用すると、複数のカテゴリのテストを同時に実行したり、実行するテストを複数のカテゴリに属するテストに限定したりすることができます。 また、テスト メソッドを作成するときにテスト カテゴリの追加が容易になり、テスト メソッドの作成後にテスト リストを保守する必要がありません。 テスト カテゴリを使用すれば、テスト リストを保守する **\<ソリューション名>.vsmdi** ファイルのチェックインおよびチェックアウトを行う必要がなくなります。 詳細については、「[テスト カテゴリの定義によるテストのグループ化](/devops-test-docs/test/defining-test-categories-to-group-your-tests)」を参照してください。|-   テスト リストを使用する既存のテスト プロジェクトとの互換性を維持するために、依然として Visual Studio を使用して .vsmdi ファイルを編集することができます。<br />-   移行されたテスト リストを Visual Studio で実行することはできませんが、コマンド ラインから mstest.exe を使用すればそれらを実行することができます。 詳細については、「[MSTest を使用したコマンド ラインからの自動テストの実行](/devops-test-docs/test/run-automated-tests-from-the-command-line-using-mstest)」を参照してください<br />-   ビルド定義でテスト リストを使用していた場合、テスト リストを使用し続けることができます。 詳細については、「[方法: アプリケーションのビルド後にスケジュールされているテストを構成および実行する](http://msdn.microsoft.com/en-us/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd)」および「[ビルド プロセスでのテストの実行](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)」を参照してください。|  
|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ではプライベート アクセサーは使用されていません。<br /><br /> Visual Studio の以前のバージョンでは、Publicize を使用して内部アプリケーション プログラミング インターフェイス (API) を指定し、対になる公開 API を作成できました。それをテストで呼び出して、製品の内部 API を呼び出すことができました。 次いで、コード生成を使用してテスト スタブを作成し、そのスタブ内にコード スニペットを生成することができました。|プライベート アクセサーを作成できなくなります。|<ul><li>Visual Studio 2010 テスト プロジェクトは [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] でコンパイルして使用できます。 ビルドには出力の警告が含まれます。</li><li>依然として内部 API をテストする必要がある場合は、次のオプションがあります。<br /><br /> <ul><li><xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> クラスを使用して、コードの内部 API およびプライベート API へのアクセスを支援します。 これは Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll アセンブリ内にあります。</li><li>コードを反映できるリフレクション フレームワークを作成して、内部 API またはプライベート API にアクセスします。</li><li>アクセスしようとしているコードが内部コードの場合、テスト コードが内部 API にアクセスできるよう <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> を使用すれば API にアクセスできる可能性があります。</li></ul></li></ul>|  
|テストの影響は削除されます|||  
|テスト エクスプローラーからの TRX ログによる実行結果の共有。||TRX ログは、依然としてコマンド ラインおよびチーム ビルドから取得できます。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio プロジェクトの移植、移行、およびアップグレード](../porting/port-migrate-and-upgrade-visual-studio-projects.md)   
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [旧バージョンの Visual Studio からのテストのアップグレード](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Visual Studio 2010 からのコード化された UI テストのアップグレード](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
