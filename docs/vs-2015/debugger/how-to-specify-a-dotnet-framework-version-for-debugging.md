---
title: '方法: デバッグで .NET Framework のバージョンの指定 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a07975591525f9109fecfbfb5aaa27642fc9562
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536998"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>方法 : デバッグで .NET Framework のバージョンを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: .NET Framework のバージョンのデバッグを指定](https://docs.microsoft.com/visualstudio/debugger/how-to-specify-a-dotnet-framework-version-for-debugging)します。  
  
[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] デバッガーでは、Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の現在のバージョンだけでなく、古いバージョンのデバッグもサポートしています。 Visual Studio からアプリケーションを起動する場合、デバッガーの正しいバージョンに常に識別できます、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]をデバッグするアプリケーション。 使用すると、アプリケーションが既に実行されている**にアタッチ**、デバッガーは常にできないことがありますの以前のバージョンを識別するために、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。 この場合、次のようなエラー メッセージが出力されます。  
  
 "アプリケーションが使用しようとしている Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] のバージョンに関してデバッガーが不適切な想定を行っています。"  
  
 このような場合はまれですが、使用するデバッガーのバージョンを指定するには、レジストリ キーを設定します。  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>デバッグで .NET Framework のバージョンを指定するには  
  
1.  コンピューターにインストールされている .NET Framework のバージョンを確認するには、Windows\Microsoft.NET\Framework ディレクトリを探します。 バージョン番号は次のようになります。  
  
     `V1.1.4322`  
  
     正しいバージョン番号を確認し、メモしておきます。  
  
2.  開始、**レジストリ エディター** (regedit)。  
  
3.  **レジストリ エディター**HKEY_LOCAL_MACHINE フォルダーを開きます。  
  
4.  移動します: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449ec4cc-30d2-4032-9256-ee18eb41b62b}  
  
     キーが存在しない場合、HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine を右クリックし、クリックして**新しいキー**します。 新しいキーの名前`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`します。  
  
5.  {449ec4cc-30d2-4032-9256-ee18eb41b62b} に移動し、検索、**名前**列、および、CLRVersionForDebugging キーを検索します。  
  
    1.  キーが存在しない場合、{449ec4cc-30d2-4032-9256-ee18eb41b62b} を右クリックし、クリックして**新しい文字列値**します。 新しい文字列値を右クリックし、をクリックして**の名前を変更**、および種類`CLRVersionForDebugging`します。  
  
6.  ダブルクリック**CLRVersionForDebugging**します。  
  
7.  **文字列の編集**ボックスに、.NET Framework のバージョン番号を入力、**値**ボックス。 たとえば、「V1.1.4322」などです。  
  
8.  **[OK]** をクリックします。  
  
9. 閉じる、**レジストリ エディター**します。  
  
     それでもデバッグの開始時にエラー メッセージが表示される場合は、レジストリに正しいバージョン番号が入力されていることを確認します。 また、Visual Studio でサポートされている [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] のバージョンを使用していることを確認します。 デバッガーは、現在のバージョンおよび以前のバージョンの .NET Framework と互換性がありますが、将来のバージョンとの上位互換性はない可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)



