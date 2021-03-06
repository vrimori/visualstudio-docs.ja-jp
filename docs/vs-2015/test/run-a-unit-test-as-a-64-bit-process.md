---
title: 64 ビット プロセスとして単体テストを実行する | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ce0c3e897795e231097f6364be19576358f5ea4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784629"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

64 ビット コンピューターの場合、単体テストを実行し、64 ビット プロセスとしてコード カバレッジ情報を取得できます。  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行する  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>64 ビット プロセスとして単体テストを実行するには  
  
1.  コードまたはテストを 32 ビット/x86 としてコンパイルされたが、それを 64 ビット プロセスとして実行する場合、**任意の CPU** として再コンパイルします。あるいは任意で **64 ビット**として再コンパイルします。  
  
    > [!TIP]
    >  柔軟性を最大限に高めるには、テスト プロジェクトを**任意の CPU** 構成でコンパイルします。 これにより、32 ビット エージェントと 64 ビット エージェントの両方で実行できます。 **64 ビット**構成でテスト プロジェクトをコンパイルしても、特に利点はありません。  
  
2.  Visual Studio メニューから、**[テスト]** を選択し、**[設定]** を選択し、**[プロセッサ アーキテクチャ]** を選択します。 64 ビット プロセスとしてテストを実行するには、**[x64]** を選択します。  
  
     \- または  
  
     .runsettings ファイルに `<TargetPlatform>x64</TargetPlatform>` を指定します。 この方法の長所は、さまざまなファイルに設定のグループを指定し、設定を簡単に切り替えられることです。 ソリューション間で設定をコピーすることもできます。 詳細については、「[.runsettings ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)」をご覧ください。  
  
## <a name="see-also"></a>「  
 [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)   
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [Visual Studio のテストにおけるテスト設定の指定](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
