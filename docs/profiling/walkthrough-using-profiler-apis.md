---
title: "チュートリアル : プロファイラー API の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パフォーマンス ツール, チュートリアル"
  - "プロファイル ツール, チュートリアル"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# チュートリアル : プロファイラー API の使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、C\# アプリケーションを使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツール API を使用する方法を示します。  プロファイラー API を使用して、インストルメンテーション プロファイリング中に収集されるデータの量を制限します。  
  
 このチュートリアルの手順は、通常、C\/C\+\+ アプリケーションにも当てはまります。  言語ごとに、ビルド環境を正しく構成しておく必要があります。  
  
 通常は、サンプル プロファイルを使用して、アプリケーションのパフォーマンス分析を開始します。  サンプル プロファイルでボトルネックを特定する情報が提供されない場合は、インストルメンテーション プロファイリングでより詳細な情報を提供できます。  インストルメンテーション プロファイリングは、スレッドの対話を調査するのに非常に便利です。  
  
 ただし、情報がより詳細になるため、収集されるデータが多くなります。  インストルメンテーション プロファイリングでは大きなデータ ファイルが作成されることがあります。  また、インストルメンテーションは、アプリケーションのパフォーマンスに影響を与える可能性が高くなります。  詳細については、「[インストルメンテーション データ値について](../profiling/understanding-instrumentation-data-values.md)」および「[サンプリング データ値について](../profiling/understanding-sampling-data-values.md)」を参照してください。  
  
 Visual Studio プロファイラーでは、データの収集を制限できます。  このチュートリアルでは、プロファイラー API を使用してデータの収集を制限する方法の例を示します。  Visual Studio プロファイラーでは、アプリケーション内からデータの収集を制御する API を提供しています。  
  
 ネイティブ コードの場合、Visual Studio プロファイラー API は VSPerf.dll 内にあります。  ヘッダー ファイル VSPerf.h とインポート ライブラリ VSPerf.lib が Microsoft Visual Studio 9\\Team Tools\\Performance Tools ディレクトリに格納されています。  
  
 マネージ コードの場合、プロファイラー API は、Microsoft.VisualStudio.Profiler.dll. 内にあります。  この DLL は、Microsoft Visual Studio 9\\Team Tools\\Performance Tools ディレクトリにあります。  詳細については、「<xref:Microsoft.VisualStudio.Profiler>」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルは、使用する開発環境が、デバッグとサンプリングをサポートするように構成されていることを前提としています。  以下のトピックでは、これらの前提条件についての概要を説明します。  
  
 [方法 : 収集方法を選択する](../profiling/how-to-choose-collection-methods.md)  
  
 [方法: Windows シンボル情報を参照する](../profiling/how-to-reference-windows-symbol-information.md)  
  
 既定では、プロファイラーを開始すると、グローバル レベルでデータが収集されます。  プログラムの先頭に以下のコードがあると、グローバル プロファイルは無効になります。  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 API 呼び出しを使用せずに、コマンド ラインでデータの収集を無効にすることができます。  以下の手順では、コマンド ライン ビルド環境が開発ツールとプロファイリング ツールを実行するように構成されていることを前提としています。  これには、VSInstr および VSPerfCmd に必要な設定が含まれます。  「コマンド ライン プロファイル ツール」を参照してください。  
  
## プロファイラー API を使用したデータ収集の制限  
  
#### プロファイリングするコードを作成するには  
  
1.  使用している設定に応じて、Visual Studio で新しい C\# プロジェクトを作成するか、コマンド ライン ビルドを使用します。  
  
    > [!NOTE]
    >  ビルドは Microsoft.VisualStudio.Profiler.dll ライブラリを参照する必要があります。これは、Microsoft Visual Studio 9\\Team Tools\\Performance Tools ディレクトリに格納されています。  
  
2.  次のコードをコピーし、プロジェクトに貼り付けます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### Visual Studio IDE でデータを収集して表示するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE を開きます。  **\[分析\]** メニューの **\[プロファイラー\]** をポイントし、**\[新しいパフォーマンス セッション\]** をクリックします。  
  
2.  コンパイル済みバイナリを **\[パフォーマンス エクスプローラー\]** ウィンドウの **\[ターゲット\]** リストに追加します。  **\[ターゲット\]** を右クリックし、**\[ターゲット バイナリの追加\]** をクリックします。  **\[ターゲット バイナリの追加\]** ダイアログ ボックスでバイナリを見つけ、**\[開く\]** をクリックします。  
  
3.  **パフォーマンス エクスプローラー**のツール バーの **\[メソッド\]** リストから **\[インストルメンテーション\]** を選択します。  
  
4.  **\[プロファイルを使用して起動\]** をクリックします。  
  
     プロファイラーはバイナリをインストルメント化して実行し、パフォーマンス レポート ファイルを作成します。  **パフォーマンス エクスプローラー**の **\[レポート\]** ノードに、パフォーマンス レポート ファイルが表示されます。  
  
5.  表示されたパフォーマンス レポート ファイルを開きます。  
  
 既定では、プロファイラーを開始すると、グローバル レベルでデータが収集されます。  プログラムの先頭に以下のコードがあると、グローバル プロファイルは無効になります。  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### コマンド ラインでデータを収集して表示するには  
  
1.  このチュートリアルで前述した「プロファイリングするコードを作成するには」の手順で作成したサンプル コードのデバッグ バージョンをコンパイルします。  
  
2.  マネージ アプリケーションのプロファイリングを行う場合は、次のコマンドを入力して、適切な環境変数を設定します。  
  
     VsPefCLREnv \/traceon  
  
3.  次のコマンドを入力します。: VSInstr \<filename.exe\>  
  
4.  次のコマンドを入力します。: \/start:trace VSPerfCmd \/output:\<filename.vsp\>  
  
5.  次のコマンドを入力します。VSPerfCmd \/globaloff  
  
6.  プログラムを実行します。  
  
7.  次のコマンドを入力します。VSPerfCmd \/shutdown  
  
8.  次のコマンドを入力します。: VSPerfReport \/calltrace:\<filename.vsp\>  
  
     結果のパフォーマンス データと共に、現在のディレクトリに .csv ファイルが作成されます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Visual Studio プロファイラー API リファレンス \(ネイティブ\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [作業の開始](../profiling/getting-started-with-performance-tools.md)   
 [コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)