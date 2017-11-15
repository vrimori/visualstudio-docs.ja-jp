---
title: "64 ビット プロセスとして単体テストを実行する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: "25"
ms.author: douge
manager: douge
ms.openlocfilehash: bb22521dc0c4f4a1a824c3554ce37297a61108c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行する
64 ビット コンピューターの場合、単体テストを実行し、64 ビット プロセスとしてコード カバレッジ情報を取得できます。  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行する  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行するには  
  
1.  コードまたはテストを 32 ビット/x86 としてコンパイルされたが、それを 64 ビット プロセスとして実行する場合、**任意の CPU** として再コンパイルします。あるいは任意で **64 ビット**として再コンパイルします。  
  
    > [!TIP]
    >  柔軟性を最大限に高めるには、テスト プロジェクトを**任意の CPU** 構成でコンパイルします。 これにより、32 ビット エージェントと 64 ビット エージェントの両方で実行できます。 **64 ビット**構成でテスト プロジェクトをコンパイルしても、特に利点はありません。  
  
2.  Visual Studio メニューから、**[テスト]** を選択し、**[設定]** を選択し、**[プロセッサ アーキテクチャ]** を選択します。 64 ビット プロセスとしてテストを実行するには、**[x64]** を選択します。  
  
     \- または  
  
     .runsettings ファイルに `<TargetPlatform>x64</TargetPlatform>` を指定します。 この方法の長所は、さまざまなファイルに設定のグループを指定し、設定を簡単に切り替えられることです。 ソリューション間で設定をコピーすることもできます。 詳細については、「[.runsettings ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)   
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [Visual Studio のテストにおけるテスト設定の指定](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)
