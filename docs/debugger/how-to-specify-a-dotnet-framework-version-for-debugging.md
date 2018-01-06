---
title: "方法: デバッグ用の .NET Framework のバージョンの指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 69fa33ac76f39f7f37cc9aa84d61fd3cf7b0fe45
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>方法 : デバッグで .NET Framework のバージョンを指定する
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] デバッガーでは、Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の現在のバージョンだけでなく、古いバージョンのデバッグもサポートしています。 デバッガーが適切なバージョンを常に特定できます Visual Studio からアプリケーションを起動する場合、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]デバッグしているアプリケーションにします。 使用すると、アプリケーションが既に実行されている**にアタッチ**、デバッガー常にできないことがありますの古いバージョンを識別する、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]です。 この場合、次のようなエラー メッセージが出力されます。  
  
 "アプリケーションが使用しようとしている Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンに関してデバッガーが不適切な想定を行っています。"  
  
 このような場合はまれですが、使用するデバッガーのバージョンを指定するには、レジストリ キーを設定します。  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>デバッグで .NET Framework のバージョンを指定するには  
  
1.  コンピューターにインストールされている .NET Framework のバージョンを確認するには、Windows\Microsoft.NET\Framework ディレクトリを探します。 バージョン番号は次のようになります。  
  
     `V1.1.4322`  
  
     正しいバージョン番号を確認し、メモしておきます。  
  
2.  開始、**レジストリ エディター** (regedit)。  
  
3.  **レジストリ エディター**HKEY_LOCAL_MACHINE フォルダーを開きます。  
  
4.  移動: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449ec4cc-30d2-4032-9256-ee18eb41b62b}  
  
     キーが存在しない場合、HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine を右クリックし、クリックして**新しいキー**です。 新しいキーの名前`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`です。  
  
5.  {449ec4cc-30d2-4032-9256-ee18eb41b62b} に移動すた後、ファイルの場所、**名前**列、および検索して、CLRVersionForDebugging キー。  
  
    1.  キーが存在しない場合、{449ec4cc-30d2-4032-9256-ee18eb41b62b} を右クリックし、クリックして**新しい文字列値**です。 新しい文字列値を右クリックし、をクリックして**の名前を変更**、および種類`CLRVersionForDebugging`です。  
  
6.  ダブルクリックして**CLRVersionForDebugging**です。  
  
7.  **文字列の編集**ボックスに、.NET Framework のバージョン番号を入力、**値**ボックス。 たとえば、「V1.1.4322」などです。  
  
8.  **[OK]**をクリックします。  
  
9. 閉じる、**レジストリ エディター**です。  
  
     それでもデバッグの開始時にエラー メッセージが表示される場合は、レジストリに正しいバージョン番号が入力されていることを確認します。 また、Visual Studio でサポートされている [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のバージョンを使用していることを確認します。 デバッガーは、現在のバージョンおよび以前のバージョンの .NET Framework と互換性がありますが、将来のバージョンとの上位互換性はない可能性があります。  
  
## <a name="see-also"></a>参照  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)