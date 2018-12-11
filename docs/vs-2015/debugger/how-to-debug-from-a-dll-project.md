---
title: '方法: DLL プロジェクトからデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61ccfc1fbf97dc36ed0625f95f998f9b154fd68c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796260"
---
# <a name="how-to-debug-from-a-dll-project"></a>方法 : DLL プロジェクトからデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DLL プロジェクトのデバッグを開始するには、プロジェクトのプロパティで呼び出し元のアプリケーションを指定する必要があります。 C++ のプロパティ ページは、C# と Visual Basic のプロパティ ページとレイアウトおよび内容が異なります。  
  
 マネージド DLL がネイティブ コードによって呼び出され、両方をデバッグする場合は、このプロジェクトのプロパティで指定できます。 詳細については、「 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)」を参照してください。  
  
> [!NOTE]
>  Visual Studio の Express Edition では、外部の呼び出し元アプリケーションを指定できません。 代わりに、実行可能なプロジェクトをソリューションに追加することが必要です。次に、これをスタートアップ プロジェクトとして設定し、実行可能なプロジェクトから DLL のメソッドを呼び出します。  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>C++ プロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**選択**プロパティ**します。 移動して、**デバッグ**タブ。  
  
2.  確認、**構成**にウィンドウの上部にあるフィールドが設定されている**デバッグ**します。  
  
3.  移動して**構成プロパティ/デバッグ**します。  
  
4.  **起動するデバッガー**一覧で、選択**ローカル Windows デバッガー**または**リモート Windows デバッガー**します。  
  
5.  **コマンド**または**リモート コマンド**ボックスで、アプリケーションの完全修飾パス名を追加します。  
  
6.  必要なプログラム引数を追加、**コマンド引数**ボックス。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>C# または Visual Basic のプロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**選択**プロパティ**します。 移動して、**デバッグ**タブ。  
  
     選択**外部プログラムの開始**を実行するプログラムの完全修飾パス名を追加します。  
  
     外部プログラムのコマンドライン引数を追加する必要がある場合にそれらを追加、**コマンドライン引数**フィールド。  
  
2.  URL としてアプリケーションを呼び出すこともできます。 ローカル ASP.NET アプリケーションが使用するマネージド DLL をデバッグする場合は、この手順を実行します。  
  
     **開始動作**を選択、 **URL でブラウザーを開始:** オプション ボタンをクリックし、URL を入力します。  
  
### <a name="to-start-debugging-from-the-dll-project"></a>DLL プロジェクトからデバッグを開始するには  
  
1.  必要に応じてブレークポイントを設定します。  
  
2.  デバッグを開始 (f5 キーを押して、緑色の矢印をクリックしてまたはクリックして**デバッグ]/[デバッグの開始**)。  
  
## <a name="see-also"></a>関連項目  
 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)



