---
title: "タスクの作成 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: "19"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92571ff82424d47875b4f28873c02ca9bdd3c237
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="task-writing"></a>タスクの作成
タスクでは、ビルド プロセスの間に実行するコードを指定します。 タスクはターゲットに含まれます。 一般的なタスクのライブラリは [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に付属します。独自のタスクを作成することもできます。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に付属するタスク ライブラリの詳細については、[タスク リファレンス](../msbuild/msbuild-task-reference.md)を参照してください。  
  
## <a name="tasks"></a>[タスク]  
 タスクには、1 つまたは複数のファイルをコピーする [Copy](../msbuild/copy-task.md)、ディレクトリを作成する [MakeDir](../msbuild/makedir-task.md)、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ソース コード ファイルをコンパイルする [Csc](../msbuild/csc-task.md) などがあります。 各タスクは、Microsoft.Build.Framework.dll アセンブリで定義されている <xref:Microsoft.Build.Framework.ITask> インターフェイスを実装する .NET クラスとして実装されます。  
  
 タスクを実装するには 2 つの方法があります。  
  
-   <xref:Microsoft.Build.Framework.ITask> インターフェイスを直接実装します。  
  
-   Microsoft.Build.Utilities.dll アセンブリで定義されているヘルパー クラス <xref:Microsoft.Build.Utilities.Task> からクラスを継承します。 Task は ITask を実装し、一部の ITask メンバーの既定の実装を提供します。 また、ログは簡単に記録できます。  
  
 いずれの場合でも、クラスを `Execute` という名前のメソッドに追加する必要があります。これは、タスクの実行時に呼び出されるメソッドです。 このメソッドはパラメーターを取らず、`Boolean` 値を返します。タスクが成功した場合は `true` を、失敗した場合は `false` を返します。 次は、何のアクションも実行せず、`true` を返すタスクの例です。  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 次のプロジェクト ファイルはこのタスクを実行します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 タスクが実行されるとき、タスク クラスで .NET プロパティを作成する場合、プロジェクト ファイルからも入力を受け取ります。 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、タスクの `Execute` メソッドを呼び出す直前にこれらのプロパティを設定します。 文字列プロパティを作成するには、次のようなタスク コードを使用します。  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 次のプロジェクト ファイルはこのタスクを実行し、与えられた値に `MyProperty` を設定します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>タスクの登録  
 プロジェクトがタスクを実行する場合、タスク クラスが含まれるアセンブリを見つける方法を [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に与えている必要があります。 タスクは [UsingTask 要素 (MSBuild)](../msbuild/usingtask-element-msbuild.md) で登録されます。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ファイルの Microsoft.Common.Tasks は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に付属するすべてのタスクを登録する `UsingTask` 要素の一覧が含まれるプロジェクト ファイルです。 このファイルは、あらゆるプロジェクトのビルド時に自動的に追加されます。 Microsoft.Common.Tasks に登録されているタスクが現在のプロジェクト ファイルにも登録されている場合、現在のプロジェクト ファイルに優先権が与えられます。つまり、既定のタスクが、同じ名前を持つ独自のタスクでオーバーライドされます。  
  
> [!TIP]
>  Microsoft.Common.Tasks のコンテンツを表示することで、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に付属するタスクの一覧を確認できます。  
  
## <a name="raising-events-from-a-task"></a>タスクからイベントを生成する  
 タスクが <xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生する場合、<xref:Microsoft.Build.Utilities.Task> クラスで次のいずれかのヘルパー メソッドを利用して生成したイベントは、登録されているあらゆるロガーで記録され、表示されます。  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 このようなイベントは、タスクが <xref:Microsoft.Build.Framework.ITask> を直接実装する場合でも生成できますが、IBuildEngine インターフェイスを利用する必要があります。 次は、ITask を実装し、カスタム イベントを生成するタスクの例です。  
  
```csharp
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="requiring-task-parameters-to-be-set"></a>タスク パラメーターの設定を要求する  
 特定のタスク プロパティを "必須" に設定できます。必須にすると、タスクを実行するプロジェクト ファイルで、必須のプロパティに値を設定する必要があります。設定しないと、ビルドに失敗します。 次のように、タスクの .NET プロパティに `[Required]` 属性を適用します。  
  
```csharp
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` 属性は <xref:Microsoft.Build.Framework> 名前空間の <xref:Microsoft.Build.Framework.RequiredAttribute> によって定義されます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生されるタスクを示します。 このタスクは成功を示す `true` を返します。  
  
### <a name="code"></a>コード  
  
```csharp
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Framework.ITask> インターフェイスを実装するタスクを示します。 このタスクは成功を示す `true` を返します。  
  
### <a name="code"></a>コード  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 この [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生されるタスクを示します。 必須の文字列プロパティがあり、登録されているすべてのロガーで表示されるイベントを生成します。  
  
### <a name="code"></a>コード  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次は、前のサンプル タスク SimpleTask3 を呼び出すプロジェクト ファイルの例です。  
  
### <a name="code"></a>コード  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>参照  
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)   
 [Task Reference (タスク リファレンス)](../msbuild/msbuild-task-reference.md)