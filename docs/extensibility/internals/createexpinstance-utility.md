---
title: "CreateExpInstance ユーティリティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "実験用ビルド"
  - "実験用ハイブ"
  - "実験用インスタンス"
  - "createexpinstance"
  - "createexpinst"
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# CreateExpInstance ユーティリティ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

リセットすると、作成するに CreateExpInstance ユーティリティを使用するか、Visual Studio の実験用インスタンスを削除します。 実験用インスタンスを使用して、デバッグし、基になる製品を変更することがなく Visual Studio 拡張機能をテストすることができます。  
  
## 構文  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### パラメーター  
 \/作成します。  
 実験用インスタンスを作成します。  
  
 \/リセット  
 実験用インスタンスを削除し、新しいものを作成します。  
  
 \/Clean  
 実験用インスタンスを削除します。  
  
 \/VSInstance  
 コピーする基本の Visual Studio インスタンスを格納するディレクトリの名前。  
  
 \/RootSuffix  
 実験用インスタンスのディレクトリの名前に追加するサフィックスです。  
  
## 解説  
 Visual Studio 拡張機能で作業するときに既定の実験用インスタンスを開き、現在の拡張機能のインストールに F5 キーを押します。 実験用インスタンスが使用できない場合は、既定の設定がある 1 つが作成されます。  
  
 実験用インスタンスの既定の場所は、Visual Studio のバージョン番号に依存します。 たとえば、Visual Studio 2015 での場所は、%localappdata%\\Microsoft\\VisualStudio\\14.0Exp\\ ディレクトリ内のすべてのファイルはそのインスタンスの一部と見なされます。 既定の場所にディレクトリ名を変更しない限り、任意の追加の実験用インスタンスは Visual Studio によって読み込まれません。  
  
 Visual Studio が開くと、実験用インスタンスのシステム レジストリにアクセスしません。 これは、レジストリ ハイブの実験用のバージョンを使用する Visual Studio の以前のバージョンによって異なります。  
  
 CreateExpInstance ユーティリティには、VsRegEx ユーティリティが置き換えられます。  
  
 次の例では、Visual Studio の既定の実験用インスタンスをリセットします。  
  
 **CreateExpInstance.exe\/Reset\/VSInstance \= 14.0\/RootSuffix Exp を \=**  
  
## 参照  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)