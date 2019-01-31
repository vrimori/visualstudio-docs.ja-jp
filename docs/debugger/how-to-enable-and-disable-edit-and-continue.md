---
title: '方法: 有効にして、エディット コンティニュを無効にする |Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: a201dab58084476f0993304d961fc5afa5693782
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002230"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>方法: 有効にして、エディット コンティニュを無効にする (C#、VB、C++)

無効にするか、有効にする**エディット コンティニュ**Visual Studio で**オプション**デザイン時にダイアログ ボックス。 **エディット コンティニュ**はデバッグ ビルドでのみ動作します。 詳細については、「[エディット コンティニュ](../debugger/edit-and-continue.md)」を参照してください。 
  
ネイティブの c++**エディット コンティニュ**を使用する必要があります、`/INCREMENTAL`オプション。 C++ では、機能要件の詳細については、この参照してください[ブログの投稿](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)と[エディット コンティニュ (Visual C)](../debugger/edit-and-continue-visual-cpp.md)します。
  
**有効または、エディット コンティニュを無効にします。**  
  
1.  デバッグ セッションの場合は、デバッグを停止 (**デバッグ** > **デバッグの停止**または**Shift**+**F5**).

1.  **ツール** > **オプション**> (または**デバッグ** > **オプション**) > **のデバッグ** > **全般**、**エディット コンティニュ**右側のウィンドウで。  
  
    > [!NOTE]
    >  IntelliTrace が有効になっている場合に、IntelliTrace イベントと呼び出し情報の両方を収集すると、エディット コンティニュが無効になります。 詳細については、次を参照してください。 [IntelliTrace](../debugger/intellitrace.md)します。
    
1.  C++ コードのことを確認します**を有効にするネイティブ エディット コンティニュ**を選択すると、し、追加のオプションを設定します。
    - **[コンティニュに変更を適用する (ネイティブのみ)]**  
      
      選択した場合、Visual Studio は自動的にコンパイルし、中断状態からデバッグを続行する場合は、コードの変更を適用します。 それ以外の場合を使用して変更を適用できます**デバッグ** > **コード変更を適用**します。  
      
    - **[古いコードの警告を表示する (ネイティブのみ)]**  
      
      選択した場合、古いコードに関する警告を示します。 
  
1.  **[OK]** をクリックします。    
