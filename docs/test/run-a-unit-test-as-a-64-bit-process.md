---
title: "64 ビット プロセスとして単体テストを実行する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "単体テスト, 作成"
  - "単体テスト, 実行"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "mlearned"
manager: "douge"
---
# 64 ビット プロセスとして単体テストを実行する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

64 ビット コンピューターを使用している場合は、64 ビット プロセスとして単体テストをキャプチャのコード カバレッジ情報を実行できます。  
  
## 64 ビット プロセスとしての単体テストの実行  
  
#### 64 ビット プロセスとして単体テストを実行するには  
  
1.  32 ビット x86 としてコンパイル済みのコードまたはテストを 64 ビット プロセスとして実行することが必要な場合、**"Any CPU"** またはオプションで **"64 ビット"** として再コンパイルします。  
  
    > [!TIP]
    >  柔軟性を最大限に高めるには、テスト プロジェクトを **"Any CPU2"** 構成でコンパイルします。  これにより、32 ビット エージェントと 64 ビット エージェントの両方で実行できます。  **"64 ビット"** 構成でテスト プロジェクトをコンパイルしても、特に利点はありません。  
  
2.  Visual Studio メニューで、**\[テスト\]** をクリックします、**\[設定\]** をクリックします、**\[プロセッサ アーキテクチャ\]** をクリックします。  64 ビット プロセスとしてテストを実行するに **\[x64\]** をクリックします。  
  
     または  
  
     .runsettings ファイルで `<TargetPlatform>x64</TargetPlatform>` を指定します。  このメソッドの利点は、異なるファイルで設定のグループを選択し、設定の間をすばやく切り替えることができます。  また、ソリューション間で設定をコピーできます。  詳細については、「[.runsettings ファイルを使用して単体テストを構成する](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)」を参照してください。  
  
## 参照  
 [テスト エクスプローラーを使用して単体テストを実行する](../test/run-unit-tests-with-test-explorer.md)   
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [Visual Studio のテストにおけるテスト設定の指定](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)