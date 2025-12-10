### import { Suspense } from "react";
So it is basically used to pause the rendering the parts of UI until some async operation has finished.
- Note : So we can say that it allow us to handle asynchronous operations in the UI more effectively.
- It helps us to manage the loading state declaratively instead of using the isLoading flags everywhere.
- Suspend basically means delay rendering.
- While the component is suspended, react will show the Fallback UI define inside the <Suspense></Suspense>
```
<Suspense fallback={<LoadingSpinner />}>
  <SomeAsyncComponent />
</Suspense>
```

## Use Cases
### 1. Lazy Loading Components
- React provides `React.lazy()` to dynamically import components only when needed.
```
import { Suspense, lazy } from "react";
const profile = lazy(() => import("./Profile"));

function App() {
	return (
		<div>
			<h1>Welcome</h1>
			<Suspense fallback={<p>Loading Profile...</p>}>
				<Profile />
			</Suspense>
		</div>
	)
}
```

### 2. Fetching Data


